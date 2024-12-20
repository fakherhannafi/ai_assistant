Fakher's Assistant UI

<p align="center">
<img src="src/app/public/clara.png" alt="drawing" width="200"/>
</p>


## Prerequisites
* Docker Engine (Docker Desktop Windows, etc...)
* Python ^3.9

## Import Model
```shell
cd src
```

## activate Venv
```shell
$ source d:/code/ai_assistant/.venv/Scripts/activate
```

## Install Poetry to manage package instead of pip
```shell
pip install poetry
```

## Install Poetry to manage package instead of pip
```shell
poetry lock
```

## Install Poetry to manage package instead of pip
```shell
poetry install
```

## Start App in local with Hot Reload
```shell
chainlit run app/main.py -w
```


## Build Docker Image : 1- Set ECR registry
Retrieve an authentication token and authenticate your Docker client to your registry. Use the AWS CLI:
```shell
aws ecr get-login-password --region eu-west-1 | docker login --username AWS --password-stdin 102184989743.dkr.ecr.eu-west-1.amazonaws.com
```


## Build Docker Image : 2- Build new image version with docker
Build your Docker image using the following command. For information on building a Docker file from scratch see the instructions here . You can skip this step if your image is already built:
```shell
docker build -t assistant .
```

## Build Docker Image : 3- Run and Test in local
Run the following command to push this image to your newly created AWS repository 
PI: make sure you are on project root folder to get .env file
```shell
docker run  --env-file .env assistant
```

## Build Docker Image : 4- Tag Image
After the build completes, tag your image so you can push the image to this repository
```shell
docker tag assistant:latest 102184989743.dkr.ecr.eu-west-1.amazonaws.com/assistant:latest
```

## Build Docker Image : 5- Push to ECR
Run the following command to push this image to your newly created AWS repository:
```shell
docker push 102184989743.dkr.ecr.eu-west-1.amazonaws.com/assistant:latest
```
