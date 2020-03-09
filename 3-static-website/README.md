A docker container that download host a website on port 2020.

# To build
```
Run > docker build -t 3-static-website .
Run > docker run -d -p 2020:80 3-static-website:latest
```

# To remove
```
Run > docker rm 3-static-website
```

# To stop and release the port
```
Run > docker ps -a
Run > docker container stop <container-id>
```