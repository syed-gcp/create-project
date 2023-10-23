# create-project

This action uses a service account to automate project creation. 

Note, Service accounts are not allowed to create projects outside of an organization resource and must specify the parent resource when creating a project.

Required Inputs:
  project-name:
   description: 'Name of the GCP Project'

  project-id:
    description: 'ID of the GCP Project'

  org-id:
    description: 'The ID of the Google Cloud Organization'
