# 1. CI/CD Pipeline for Flask Application Using Jenkins
---

## Description:

  1.This project demonstrates how to set up a complete CI/CD pipeline using Jenkins for a simple Flask web application.
  The pipeline automatically performs the following:
  
  2.Builds the application by installing dependencies
  
  3.Runs unit tests using pytest
  
  4.Deploys the application to a staging server if all tests pass
  
  5.Triggers automatically on every push to the "**Jenkins**" branch
  
  6.Sends email notifications on success or failure

---

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

---

 ## Source Code:
 
   After forking, the repository was cloned to the Jenkins server using:

   git clone https://github.com/imran7012/flask_Practice.git

---

 ## Jenkinsfile:

  ## Create a Jenkinsfile in the root of your Python application repository.

<img width="1320" height="826" alt="image" src="https://github.com/user-attachments/assets/c9ff6007-4c79-4496-b2c7-85f4aadb6a10" />


## Define a pipeline with the following stages:

  ## Build: Install dependencies using pip.

<img width="425" height="195" alt="image" src="https://github.com/user-attachments/assets/2c00e0ef-1845-4ffd-8be0-7d9de54358dd" />


  ## Test: Run unit tests using a testing framework like pytest.

<img width="349" height="222" alt="image" src="https://github.com/user-attachments/assets/19cab0af-9977-453c-b03b-be9f71edf7d4" />


  ## Deploy: If tests pass, deploy the application to a staging environment.

<img width="694" height="762" alt="image" src="https://github.com/user-attachments/assets/c820079b-cbf0-4638-ae98-980c1d18a9b0" />


---

 ## Pipeline Triggers:
 
   ## Steps:
    1.Open Jenkins job
    
    2.Go to Configure → Build Triggers
    
    3.Enable: GitHub hook trigger for GITScm polling
    
  <img width="778" height="665" alt="image" src="https://github.com/user-attachments/assets/3109a24b-0cb2-4cb8-92f8-343b3427f438" />

    4.Configure webhook in GitHub:
    
  <img width="1383" height="887" alt="image" src="https://github.com/user-attachments/assets/d17aee56-2548-492b-a723-9b2ff4985018" />

---

## Notifications:
 
  Email notifications are enabled using the Jenkins Email Extension Plugin.
  
  SMTP details must be configured in:
  
  Manage Jenkins → Configure System → Extended E-mail Notification

<img width="1703" height="782" alt="image" src="https://github.com/user-attachments/assets/797d1c85-4709-4fb6-9245-038b9cda719f" />

   Notifications are sent when:
  
     Build succeeds
  
     Build fails

<img width="853" height="499" alt="image" src="https://github.com/user-attachments/assets/76637a5f-5fed-46d5-8c10-e4c2d838cce0" />


<img width="1057" height="494" alt="image" src="https://github.com/user-attachments/assets/f05e154f-6988-4d27-88e7-467330718431" />



---
     
## Deployment outcome:

  https://jenkinsacademics.herovired.com/job/syed_Flask_test/

  ## Deploy-Stage Results:
  
  
  <img width="1456" height="966" alt="image" src="https://github.com/user-attachments/assets/68ed0a00-a87c-4ebc-ab42-1de49393c17f" />
  


  <img width="1483" height="601" alt="image" src="https://github.com/user-attachments/assets/d3a2f99a-2973-4968-9dcf-daad23e782e4" />


  Compass Database:
  

  <img width="1151" height="977" alt="image" src="https://github.com/user-attachments/assets/0dd79670-a061-4018-a0b6-3caefadf9c5c" />
  


---  

--- 




   



    






