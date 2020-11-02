# Docker
You can dockerize this microservice with these steps:
* Create and push the image
  ```
  docker build -t films -f Dockerfile .
  ```

* Run the image:
  ```
  docker run -d -p 5000:5000 films
  ```