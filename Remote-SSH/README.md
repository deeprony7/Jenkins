## Deploy Python Flask/Django App on remote server with Jenkins

We have a pretty simple usecase here where we need to deploy the latest source code on the remote server

Without Jenkins:
    Steps to deploy
    1. ssh to remote server
    2. checkout directory where code resides
    3. perform git pull
    4. restart service to reflect the changes

With Jenkins:
    1. 