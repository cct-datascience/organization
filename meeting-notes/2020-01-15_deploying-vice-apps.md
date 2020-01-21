# Deploying a VICE app in CyVerse Discovery Environment
## January 15, 2020

### Present
* Jorge Barrios
* Ryan Bartelme
* Emily Cain
* Tyson Swetnam

### About Tools 
* Not the same thing as the App
* Docker containers used to build the App
* Choose an existing Tool to build your App, or create your own
* Managing Tools
  * Apps --> Manage Tools
  * Can filter for just Your Tools or Public Tools
  * For basic JupyterLab functionality, can use a public tool like `cyverse/jupyterlab-scipy`
  * Can check / copy Dockerfiles on CyVerse VICE [Github](https://github.com/cyverse-vice) in the `latest` directory of a repo
  * When copying and modifying a Dockerfile, may need to change `user` and other specifications for your App
### Steps
* Need [CyVerse](cyverse.org) account
* Launch Discovery Environment 
* Create App
  * Apps --> Create New. . . 
  * Choose public or custom Tool
  * Add features as needed like input file, multiple files, or directories (these files can be hidden from App users)
  * `Container name` should be the same as `Image Name` on Dockerhub
  * `Tag` is the registry of the container
  * If `entry point` is already specified in the Dockerfile, you do not need to fill this in when creating the App on the DE
  * `UID` = container permissions within the group
  * Set container port (e.g., 8888 for JupyterLab or 8787 for Rstudio)
  * Port must be exposed in Dockerfile and also opened in VICE App
  * (Don't need to mess around with command line?)
* Save, close, and share as needed - will now show up in Your Apps
    

### Notes
* You can only have 2 apps running at once
* Once you make your app public, you will no longer be able to edit it 
* If it takes more than 5 minutes to launch a small App or Analysis, then there's probably something wrong
    * Do you already have 2 Apps or Analyses running?
* Can create Communities within CyVerse with admins and favorite Apps
* Can create Teams of users to make sharing data, Tools, and Apps with collaborators easier and also keep everything private within your Team
* No `Quick Launch` unless you create one
* Git and Github integration / widget (may need to be on `master` branch)
* Public Apps shared outside of Teams require more information / parameters to fill out
* If you don't specify an output directory when creating your App, it will go directly to your personal CyVerse Analyses
