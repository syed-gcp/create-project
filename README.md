## **create-project**

This Github Action creates a Google Cloud Project in your Organisation.


## Pre-requisites
- A Google Cloud Organisation
- Google Cloud Service Account Key in JSON format, as a GitHub secret.
- This action runs using Node 16. If you are using self-hosted GitHub Actions runners, you must use runner version  [2.285.0](https://github.com/actions/virtual-environments)  or newer.

## Usage

    jobs:   
	    job_id:
		    # ...	    
		    
    # Add "id-token" with the intended permissions.
    permissions:
      contents: 'read'
      id-token: 'write'
      
    steps:
    - name: Checkout
	- uses: 'actions/checkout@v3'
	
    - id: 'auth'
      name: 'Authenticate to Google Cloud'
      uses: 'google-github-actions/auth@v1'
      with:
        credentials_json: '${{ secrets.GOOGLE_CREDENTIALS }}'

    - name: Set up Cloud SDK
      uses: google-github-actions/setup-gcloud@v0.6.0

    - name: Create GCP Project
      uses: syed-gcp/create-project@v1
      with:
        project-name: 'your-project-name'
        project-id: 'your-project-id'
        org-id: 'your-org-id'
	  env: GOOGLE_CREDENTIALS_FILE: ${{ secrets.GOOGLE_CREDENTIALS }}

## Inputs

`project_name`: (Required) The name of your project
`project_id`: (Required) The project-id, must be [globally unique](https://cloud.google.com/resource-manager/docs/creating-managing-projects) 
`organisation`: (Required) Your organisation id