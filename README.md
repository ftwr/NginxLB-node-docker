# Load Balancing Node.js Applications with NGINX and Docker

To better understand how this works, we can run the following commands:

```
export MESSAGE=Howdy!
node index
```

After that we need to create an image, from this Dockerfile, which can be done through the following command:
```
docker build -t load-balanced-app .
```
And then we can run both instances of our application with the following commands:
```
docker run -e "MESSAGE=First instance" -p 8081:8080 -d load-balanced-app
docker run -e "MESSAGE=Second instance" -p 8082:8080 -d load-balanced-app
```
After running both commands, we will be able to open both instances on a web browser by going to http://localhost:8081 and http://localhost:8082. The first URL will show a message saying "First instance", the second URL will show a message saying "Second instance".

```
docker build -t load-balance-nginx .
docker run -p 8080:80 -d load-balance-nginx
```
