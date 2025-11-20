# 1. CI/CD Pipeline for Flask Application Using Jenkins

## Description:

  1.This project demonstrates how to set up a complete CI/CD pipeline using Jenkins for a simple Flask web application.
  The pipeline automatically performs the following:
  
  2.Builds the application by installing dependencies
  
  3.Runs unit tests using pytest
  
  4.Deploys the application to a staging server if all tests pass
  
  5.Triggers automatically on every push to the "**Jenkins**" branch
  
  6.Sends email notifications on success or failure

## Prerequisites:

 ## On Jenkins Server:

  1.Jenkins (latest LTS)
    
  2.Git plugin
    
  3.Python 3.x
    
  4.pip
    
  5.pytest
    
  6.SSH or password access to staging server
    
  7.Email Notification configured in Jenkins (SMTP settings)

 ## On Staging Server

  1.Python 3.x installed
    
  2.Required dependencies installed via requirements.txt
    
  3.Port 8000 or custom port open
    
  4.SSH access enabled
  
