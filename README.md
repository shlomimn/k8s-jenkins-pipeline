# k8s-jenkins-pipeline

# General
The Jenkinsfile is a groovy script that Jenkin CI/CD can pull and run.
This Jenkinsfile will apply K8s in stages (stage per file).

# Jenkins Pre-Requests
  * Install kubectl
    1. Download the latest release with the command:
       curl -LO "https://storage.googleapis.com/kubernetes-release/release/$(curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt)/bin/linux/amd64/kubectl"
    
    2. Make the kubectl binary executable.
       chmod +x ./kubectl
    
    3. Move the binary in to your PATH.
       sudo mv ./kubectl /usr/local/bin/kubectl
       
    4. Test to ensure the version you installed is up-to-date:
       kubectl version --client

  * Copy/Create /.kube/config to Jenkins allowing kubectl to run without sudo, 
    from Jenkins run:
    1. Make .kube directory in Jenkins
       mkdir -p $HOME/.kube
       
    2. Copy or Create the relevant ./kube/config file
       sudo cp -i /root/.kube/config $HOME/.kube/config
       or
       sudo vim $HOME/.kube/config 
       &Copy/Paste into file &Save
    
    3. Change $HOME/.kube/config to jenkins ownership
       sudo chown $(id -u):$(id -g) $HOME/.kube/config

# Jenkins 
  * Pipeline creation
    1. Create a new item in Jenkins of type *Pipeline* and give it a name.
    
    2. Go to "Pipeline" tab & Choose "Pipeline script from SCM"
       * Configure Repository URL (https://github.com/shlomimn/k8s-jenkins-pipeline)
       * Set "Branch Specifier" to main (not master)
       * Script File=Jenkinsfile (by default)
       
    3. Save & Build Now

