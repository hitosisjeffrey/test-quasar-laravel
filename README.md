# test-quasar-laravel
<p>
This project is for demonstration purposes only.
The frontend was developed using Quasar, and the backend was developed using Laravel 12.
Authentication is implemented using Laravel Passport with the password grant type.
This project follows a decoupled architecture, where the frontend and backend are developed and deployed separately.
</p>

## Prerequisite
- docker
- git
- Please make sure that the following PORTS ara available:
```
9000 - Frontend
8000 - Backend
3306 - Database
```

Development Setup

1.) In your local machine clone this repository https://github.com/hitosisjeffrey/test-quasar-laravel.git <br>
2.) Inside the test-quasar-laravel folder, clone the frontend https://github.com/hitosisjeffrey/frontend.git <br>
3.) Inside the test-quasar-laravel folder, clone the backend  https://github.com/hitosisjeffrey/backend.git <br>
Your folder structure should be similar to: <br>
![Screenshot 2025-04-11 at 5 30 46 PM](https://github.com/user-attachments/assets/1bcdf080-28db-419a-97d8-40dabb38fd45)
<br>
4.) Goto frontend and copy the .env.test to .env  <br>
5.) Goto backend and copy the .env.testing to .env   <br>
6.) Then Goto test-quasar-laravel and run the following command:
```
docker compose build && docker compose up -d
```
## backend setup database migration and seed
1.) In your terminal, run the following command. 
```
docker exec backend php artisan migrate:refresh --seed
```

Your should see the following output:
```
   INFO  Running migrations.  

  0001_01_01_000000_create_users_table .......................... 83.24ms DONE
  0001_01_01_000001_create_cache_table .......................... 26.42ms DONE
  0001_01_01_000002_create_jobs_table ........................... 68.00ms DONE
  2025_04_10_113016_create_oauth_auth_codes_table ............... 22.23ms DONE
  2025_04_10_113017_create_oauth_access_tokens_table ............ 24.33ms DONE
  2025_04_10_113018_create_oauth_refresh_tokens_table ........... 26.95ms DONE
  2025_04_10_113019_create_oauth_clients_table .................. 23.11ms DONE
  2025_04_10_113020_create_oauth_personal_access_clients_table .. 10.45ms DONE
  2025_04_10_120350_create_blogs_table .......................... 55.69ms DONE
  2025_04_11_022905_add_soft_deletes_to_blogs_table ............. 32.89ms DONE


   INFO  Seeding database.  

  Database\Seeders\UserSeeder ........................................ RUNNING  
  Database\Seeders\UserSeeder .................................. 1,031 ms DONE  

  Database\Seeders\BlogSeeder ........................................ RUNNING  
  Database\Seeders\BlogSeeder .................................... 195 ms DONE 
```
To create an Oauth Client, run the following command:
```
docker exec backend php artisan passport:client --password
```
The output should be similar to:
```
  Client ID ............................. 9ea96633-98e7-4a35-87af-1ec973b9de72  
  Client secret ..................... GoniVC4hVmeBzhMOLFrna9sR5qGJPg6XUP9FAaHL
```
Copy the Client ID and the Client secret into the frontend/.env file. (Replace the VITE_CLIENT_ID with the Client ID and the VITE_CLIENT_SECRET with the Client secret)
```
VITE_API_URL=http://127.0.0.1:8000
VITE_CLIENT_ID=9ea60e78-9677-487e-a8be-a29683c23404
VITE_CLIENT_SECRET=AEWuq88KEtmjIB8pOquWbP6ZbQML214nhW7CbIaO
```
2. Restart the frontend container and access the following URL: http://localhost:9000
3. Enter the following login details:
```
email: demo@example.com
password: password
```

## Demo Video
https://drive.google.com/file/d/1VKGLAhtoNXLUBKmplv8HaiEMdvIUa9CI/view?usp=sharing

## Screen
![Screenshot 2025-04-11 at 8 04 02 PM](https://github.com/user-attachments/assets/3dd6140f-06fa-4e03-9891-abc3f5d8009d)

## Testing
- I created a simple end to end testing for Blog 
```
docker exec backend php artisan test
```
![Screenshot 2025-04-13 at 8 42 14 AM](https://github.com/user-attachments/assets/87a9b01c-654c-4bf9-9196-27821f325398)

- I can setup the CI/CD for this as well using github workflows 
