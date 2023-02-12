# mongoose-csfle

## Deployment to Heroku using Docker image

This repository contains a docker image `Dockerfile` using node:14 as the base image. For CSFLE to function, it also requires a shared library which is compatible
with the OS running the deployment. For instance the node:14 base image uses Debian as the underlying OS, and hence the default library is downloaded from for Debian
via https://www.mongodb.com/try/download/enterprise. 

### Step 1: Download heroku CLI
Install heroku CLI using the following link - https://devcenter.heroku.com/articles/heroku-cli

### Step 2: Login in heroku container CLI
After Installing the heroku CLI, login in the heroku CLI via terminal using `heroku container:login` command, the CLI will redirect the user to the browser for login. 

### Step 3: Clone the repository
cd into the working directory and clone the repository `git clone -b csfle git@github.com:Pacifier24/mongoose-csfle.git`

### Step 4: Swtich to the team where the app is deployed
Run the following command to set the team where the heroku app is created `export HEROKU_ORGANIZATION=<team-name>`

### Step 5: Push the docker image to the heroku container registry(app name is mongoosecsfle)
Run the following command `heroku container:push web --app mongoosecsfle`

### Step 6: Release/Deploy the container image
Run the following command to release or deploy the container image, `heroku container:release web --app mongoosecsfle`

### Step 7: Check for logs to confirm if the deployment was successful 
Run the following command to check the logs `heroku logs --app mongoosecsfle`
