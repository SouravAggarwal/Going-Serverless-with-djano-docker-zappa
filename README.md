# Going-Serverless-with-djano-docker-zappa
A Basic Intorduction for going Serverless with Django + Docker + Zappa in just 10 Steps

1) Setup Django Project with Virtual Env (python 3)
* virtualenv -p python3 env
* source env/bin/activate
* django-admin startproject demo
* cd demo

2) Install necessary libraries (in virtualenv)
* pip install django zappa

2) Setup Docker and pull latest lambci/lambda image
* docker pull lambci/lambda:build-python3.6

4) Get your AWS Credentials
* Goto IAM role in AWS dashboard
* Nagivate to Users.
* Click on the Security credentials tab, and go down to Access Key
* Copy access_key_id and secret_access_key

4) Create a shortcut that allows AWS credentials to pass through to the docker container (using Environment Variables)
* alias zappashell3='docker run -ti -e AWS_SECRET_ACCESS_KEY=$AWS_SECRET_ACCESS_KEY -e AWS_ACCESS_KEY_ID=$AWS_ACCESS_KEY_ID -e AWS_DEFAULT_REGION=$AWS_DEFAULT_REGION -v $(pwd):/var/task  --rm lambci/lambda:build-python3.6 bash'
* alias zappashell3 >> ~/.bash_profile

5) Start docker container to setup virtualenv and to install dependencies
* zappashell3
* virtualenv env
* env/bin/activate
* pip install -r requirements.txt


6)
