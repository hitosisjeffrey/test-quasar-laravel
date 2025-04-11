# test-quasar-laravel

Development Setup

1.) In your local machine clone this repository https://github.com/hitosisjeffrey/test-quasar-laravel.git <br>
2.) Inside the test-quasar-laravel folder, clone the frontend https://github.com/hitosisjeffrey/frontend.git <br>
3.) Inside the test-quasar-laravel folder, clone the backend git remote add origin https://github.com/hitosisjeffrey/backend.git <br>
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
1.) Inside the backend container, (/var/www), run the following command: 
```
php artisan migrate:refresh --seed
```
To create an Oauth Client, run the following command:
```
php artisan passport:client --password
```

Copy the client_id and the secret into the frontend/.env file.
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
https://drive.google.com/file/d/1mF5IDvvWtqY7kfh5hjMfukfLAFEz6TXA/view?usp=sharing

## Notes
- I created a simple end to end testing for Blog 
```
php artisan test
```
- I can setup the CI/CD for this as well using github workflows 
