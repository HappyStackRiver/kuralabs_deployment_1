# Deployment 1
## Deployment Process (Jenkins)
1. We needed to create an EC2 with 80, 8080, 22 ports open
2. Install Jenkins Service 
  - Install dependencies (JRE and updated system)
  - Download Jenkins
  - Download Jenkins keyring
  - Update and install Jenkins
3. Configure Jenkins
  - Initially configure Jenkins
  - Install plugings
  - Create user
  - Install EC2 plugins
4. Install venv (virtual environment) for Jenkins
  - You need pip and venv (python3-pip, python3.10-venv)
5. Link GitHub to Jenkins
  - Fork the repo with the Flask App
  - Create access token for Jenkins by using GitHub client
    - admin:repo_hook
6. Jenkins Pipeline creation
  - Create a new item which is a multibranch pipeline
  - Add github as a source for the pipeline
  - Validate the source for the pipeline
  - Attempt to build the pipeline given the gitHub repository
 
## Elastic beanstalk
1. Manually download the repository onto VM machine, and zip the repository
2. Create a new environment in Elastic Beanstalk and fill out the information for you application
3. Upload your zip file
4. Deploy your application

## Explanation
What we did, was create a pipeline in Jenkins to build and test the url-shortener application. After building the pipeline and verifying that the unit tests passed, you have successfully built the pipeline. We then manually downloaded the same repository that we put into our jenkins pipeline and manually uploaded the files to an environment we created in Elastic Beanstalk to deploy into another stage.

## Issues
I personally had to refer to another documentation to properly download Jenkins, because the given keyrings and download url were not functioning for me. I personally wrote a script to make the download and install of Jenkins better, as I messed up a few of the EC2s that I wanted to host Jenkins, and it made the installation process quicker.

## Improvements
I think that looking back on the deployment, instead of manually uploading the repository, we can install the client where we built the flask app, and have it deploy using elastic beanstalk. I would recommend keeping your jenkins server but to be safe, I would also create a script to download all the dependencies that you would need to run jenkins on an instance in the case that you lose your EC2 for whatever reason.
