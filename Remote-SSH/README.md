## Deploy Python Flask/Django App on remote server with Jenkins

We have a pretty simple usecase here where we need to deploy the latest source code on the remote server

Without Jenkins:
    Steps to deploy
    1. ssh to remote server
    2. checkout directory where code resides
    3. perform git pull
    4. restart service to reflect the changes

Solution With Jenkins(without plugin):
    * Log in to jenkins master server and switch user to jenkins `su -s /bin/bash jenkins`
    Since jenkins is a service it does not have a shell by default we need to explicitly specify shell to switch
    * Check .ssh/ for id_rsa.pub, we need to share the public key with the remote server's authorized keys so it can recognize
    * Test with `ssh username@remoteHost`
    * If working alright, we need to now create a Freestyle Project on Jenkins with below configuration
        * Set `Restrict where this project can be run` to the appropirate label, ignore if only one Jenkins server
        * Under `Build` choose `Execute Shell` and in the textarea have the server ssh into remote server and execute the shell scipt within
            ```ssh username@remoteHost << EOF
                ./deploy.sh
                EOF```
    * Run your Build

You can have your shell script be a part of your SCM. 
* Use `Source Code Management` tab and set your git config.
* Under `Build` -> `Execute Shell` run scp to copy over the deploy scipt
* Execute the script like before.