## 2. GitHub Actions CI/CD for Flask Application:

  ## GitHub Actions Workflow:
  
    ├── app/
    │ └── __init__.py
    │ └── main.py
    ├── tests/
    │ └── test_example.py
    ├── requirements.txt
    ├── .github/
    │ └── workflows/
    │ └── ci-cd.yml
    └── README.md

Create the file: .github/workflows/ci-cd.yml

 <img width="870" height="908" alt="image" src="https://github.com/user-attachments/assets/2ee66a41-5cb7-4b50-b79b-9ef0fb7e9664" />


---

## Workflow Steps:
   
   This README explains how to set up and use a GitHub Actions CI/CD pipeline for a Flask-based Python web application. The pipeline:

    1.Installs dependencies
    
    2.runs unit tests with pytest
    
    3.builds an artifact
    
    4.deploys to a staging environment on pushes to the staging branch

---

## Environment Secrets:

  Store these secrets in GitHub repository settings → Secrets & variables → Actions (use exact names or update the workflow accordingly):

<img width="1685" height="881" alt="image" src="https://github.com/user-attachments/assets/675a1041-07b0-4b08-a1f4-c807dd395e07" />


---

## How the Workflow Works (step-by-step)

 ## Trigger:

  1. push to staging runs tests + Builds + deploys to staging.

  <img width="1555" height="631" alt="image" src="https://github.com/user-attachments/assets/4f691146-f062-4c82-8faf-28b662fd704c" />

--- 
  
  3. push to main runs only tests and Build steps

<img width="1878" height="852" alt="image" src="https://github.com/user-attachments/assets/6816a15c-e74b-4cf3-a7c9-4d269a2a6812" />

          
---

 ## Test and Build job:

  1.Checks out source.
  
  2.Sets up Python.
  
  3.Installs dependencies from requirements.txt.
  
  4.Runs pytest.
  
---

 ## Deploy jobs:

  1.SSH / rsync (example above)

  2.Requires an SSH keypair and a user on the target server.

  3.Use appleboy/ssh-action@v0.1.7

<img width="720" height="778" alt="image" src="https://github.com/user-attachments/assets/2c7cac96-d181-4592-b68a-2aff85139e47" />


---
 
 
 ## OutCome:


<img width="1741" height="855" alt="image" src="https://github.com/user-attachments/assets/7d48ca19-ad9d-4bb7-aaa2-64863140a89d" />






