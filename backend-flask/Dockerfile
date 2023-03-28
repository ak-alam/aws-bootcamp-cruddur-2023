FROM python:3.10-slim-buster AS compile-stage

RUN apt-get update 
RUN apt-get install -y --no-install-recommends build-essential gcc

WORKDIR /compile-stages
COPY requirements.txt .

#This will install the requirement file package binnary in the .local folder of current user's home directory
RUN pip3 install --user -r requirements.txt
ENV PATH=/root/.local/bin:$PATH

COPY . /compile-stages/


FROM python:3.10-slim-buster AS build-stage

WORKDIR /backend-flask
#Copy the compiled binnary from root user's home directory from the compile-stage to build-stage
#COPY --from=source-stage files-from-src-stage to current-stage
COPY --from=compile-stage /root/.local /root/.local
COPY --from=compile-stage /compile-stages /backend-flask/

ENV FLASK_ENV=development
#this will set path in our envirnoment so whenever a binnary needs to execute it will first look in this location /root/.local/bin
ENV PATH=/root/.local/bin:$PATH

EXPOSE ${PORT}
CMD [ "python3", "-m" , "flask", "run", "--host=0.0.0.0", "--port=4567"]
