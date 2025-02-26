# lab10

## 1.2
```
docker compose up -d

```
<img width="1184" alt="Screenshot 2568-02-25 at 03 00 15" src="https://github.com/user-attachments/assets/3f6c2bd2-7962-4ba9-8b7c-6ee36f2e7337" />


```
http://localhost:9000

```
<img width="1470" alt="Screenshot 2568-02-25 at 03 03 34" src="https://github.com/user-attachments/assets/6e58157f-3e5c-4400-ae0b-681b659ff6c5" />

## 1.3
```
docker compose down

```
## 1.4

Restart
```
docker compose up -d

```
Show Docker Volumes
```
docker volume ls

```
<img width="593" alt="Screenshot 2568-02-25 at 03 12 03" src="https://github.com/user-attachments/assets/1780af6f-ff15-4cfb-94cb-2f9046989e42" />

## 1.5 

Step 1: Shut Down the Cluster
```
docker compose down

```
Step 2: Find the Volume Name
```
docker volume ls

```
Step 3: Remove the Volume
```
docker volume rm <volume_name>
```
Step 4: Restart the Containers
```
docker compose up -d

```
Step 5: Verify the Reset
```
http://localhost:9000
```
<img width="680" alt="Screenshot 2568-02-26 at 21 00 30" src="https://github.com/user-attachments/assets/c3b7eb8f-ba9f-44d8-b62a-69f116db365d" />

<img width="1152" alt="Screenshot 2568-02-25 at 03 15 00" src="https://github.com/user-attachments/assets/5662ba73-60a5-4273-a886-4ae82baf2510" />

## 2.1
```
cd /Users/thanathorn/Desktop/Dev/lab9
```
<img width="618" alt="Screenshot 2568-02-26 at 22 25 36" src="https://github.com/user-attachments/assets/41930bb2-7916-4b44-9f0c-c88b915d8776" />
<img width="1148" alt="Screenshot 2568-02-26 at 22 26 06" src="https://github.com/user-attachments/assets/de30a965-b849-4bdc-9b35-1382da05baa1" />


## 2.2

```
docker pull thanasmp/lab9-web:latest
docker run -d -p 8080:80 thanasmp/lab9-web:latest
```
![Screenshot 2568-02-26 at 23 31 06](https://github.com/user-attachments/assets/368cd988-e255-486f-a25c-06102f325e7a)
<img width="1159" alt="Screenshot 2568-02-26 at 23 31 42" src="https://github.com/user-attachments/assets/adfc3b4c-83a0-4dbd-8281-cad954a4e8b4" />

```
http://ip:8080
```
## 2.3
1. update html
2. rebuild your docker 
```
docker build --platform linux/amd64 -t thanasmp/lab9-web:latest .
docker login
docker push thanasmp/lab9-web:latest

```

From VM

Stop and Remove the Old Container
```
docker stop id
docker rm id
```
Pull the Updated Image from Docker Hub
```
docker pull thanasmp/lab9-web:latest

```
Run the Updated Container
```
docker run -d -p 8106:80 thanasmp/lab9-web:latest
```
<img width="967" alt="Screenshot 2568-02-26 at 23 59 15" src="https://github.com/user-attachments/assets/c5bda6d0-f97a-4c4a-82fa-68e84b1faf16" />


## 2.6
```
docker buildx imagetools inspect awesomekid/my-docker-app:latest
```

![image](https://github.com/user-attachments/assets/c265f29d-df72-413b-8329-0af0d290239a)

## 3
```
docker run -d --name mongodb \
  -e MONGO_INITDB_ROOT_USERNAME=admin \
  -e MONGO_INITDB_ROOT_PASSWORD=password \
  -p 27017:27017 \
  mongo:latest
```

```
docker run -d --name mongo-express \
  -e ME_CONFIG_MONGODB_ADMINUSERNAME=admin \
  -e ME_CONFIG_MONGODB_ADMINPASSWORD=password \
  -e ME_CONFIG_MONGODB_URL="mongodb://admin:password@mongodb:27017/" \
  -p 8081:8081 \
  --link mongodb:mongo \
  mongo-express:latest
```
```
http://3.86.189.252:8081/
```
user : admin
password : pass
