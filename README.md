# nextcloud-fpm

To use: 

1. create 2 folders as follows:
   1.1. "db" folder - used to store database files from postgres
   1.2. "nextcloud" folder - used to store html and related files from app. 
2. run $ docker-compose up -d

Note:
1. You might need to change the local folders to be your owned name
2. Don't forget to change host IP address in app and collabora, this parameter would help the components know each other. 
3. Don't forget to change password. The .env file should be considered. 
