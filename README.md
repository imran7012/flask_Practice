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

<img width="1025" height="916" alt="image" src="https://github.com/user-attachments/assets/be398bc4-d923-4dbf-bcf8-ee64e45b7e47" />
