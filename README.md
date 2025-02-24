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

## 2.1
```
cd /home/prab/Documents/DevopLab/my-docker-app
```

## 2.2
```
docker pull awesomekid/my-docker-app:latest
docker run -d -p 8105:80 --name my-deployed-app awesomekid/my-docker-app:latest
```
```
http://3.86.189.252:8105
```
## 2.3
1. update html
2. rebuild your docker 
```
docker build -t awesomekid/my-docker-app:latest .
```
3. Push the Updated Image to Docker Hub
```
docker tag awesomekid/my-docker-app:latest awesomekid/my-docker-app:latest
```

```
docker push awesomekid/my-docker-app:latest
```
From VM

Stop and Remove the Old Container
```
docker stop my-deployed-app
docker rm my-deployed-app
```
Pull the Updated Image from Docker Hub
```
docker pull awesomekid/my-docker-app:latest
```
Run the Updated Container
```
docker run -d -p 8105:80 --name my-deployed-app awesomekid/my-docker-app:latest
```

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
