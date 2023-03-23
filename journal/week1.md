# Week 1 — App Containerization

In containerization week I created docker files for frontend and backend. Learned about how to build docker images. Understands how docker files are created for applications also I come to know about designing API and documenting it.

Week containerization's objective:
* docker containers
* dockerfile and docker compose

## Flask Backend:

created dockerfile for flask backend service. As our backend is written in flask python, I have used python as my base image because it comes with pre-installted python envirnoment and some basic python packages. 

**Docker Container For Backend Service**:
* Build docker image form backend directory
* Run that image on port 4567
* Check for the response from backend api endpoint by append this at the end or url '/api/activities/home'

**Creating docker build from docker file**

![docker-build](../_docs/assets/week-0/docker-build.png)


**Running the container**

![docker-build](../_docs/assets/week-0/docker-backend.png)


**Hitting the backend URL**

![backend-url](../_docs/assets/week-0/not-found.png)


**Response from backend API**

![response](../_docs/assets/week-0/backend-response.png)


## React Frontend:
Our frontend is written in react which is javascript library, I will be using node as my base image to build containers..
**Docker Container For Backend Service**:
* Build docker image form frontend directory
* Run that image on port 3000
* Check for the response from backend api endpoint by append this at the end or url '/api/activities/home'


