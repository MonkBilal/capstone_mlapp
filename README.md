
[![CircleCI](https://circleci.com/gh/MonkBilal/mlapp.svg?style=svg)](https://circleci.com/gh/MonkBilal/mlapp)
## Project Summary

In this project, I have deployed a Flask app on an AWS EKS platform. This application is a pre-trained, sklearn model that has been trained to predict housing prices in Boston according to several features, such as average rooms in a home and data about highway access, teacher-to-pupil ratios, and so on. You can read more about the data, which was initially taken from Kaggle, on the data source site. This project is using a flask app 'app.py'-that serves out predictions (inference) about housing prices through API calls.

## Setup the Environment

* Create a virtualenv and activate it
* Run `make install` to install the necessary dependencies

### Running `app.py`

1. Standalone:  `python app.py`
2. Run in Docker:  `./run_docker.sh`
3. Run in Kubernetes:  `./run_kubernetes.sh`
s
### Kubernetes Steps

* Setup and Configure Docker locally
* Setup and Configure Kubernetes locally
* Create Flask app in Container
* Run via kubectl

## Testing the app

* Run : ./make_prediction.sh <host_port>
  e.g. I'm forwarding port 8080 of my host machine to my docker container's port 80 then the script would run like : ./make_prediction.sh 8080

* Test in your browser:
  e.g http://localhost:8080


