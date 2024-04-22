# Neuroglancer Deployment

This repo contains the neuroglancer deployment

## Local usage

1. Install the docker engine
2. Clone the repo
3. Run the following command to build the docker image
```bash
cd applications/neuroglancer
sudo docker build -t neuroglancer .
```
4. Run the following command to start the docker container

```bash
sudo docker run -it --rm -d -p 8080:80 neuroglancer
```
5. Open your browser and navigate to `http://localhost:8080`
6. You should see the neuroglancer interface
7. To stop the container run the following command
```bash
sudo docker stop $(sudo docker ps -a -q --filter ancestor=neuroglancer --format="{{.ID}}")
```