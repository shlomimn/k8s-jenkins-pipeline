node {
    git branch: 'main', url: 'https://github.com/shlomimn/k8s-nodejs'
    
    stage('create K8s namespace')
    {
        sh '/usr/local/bin/kubectl apply -f namespace.yaml -n api-servers'
    }
    
    stage('create K8s secrets')
    {
        sh '/usr/local/bin/kubectl apply -f secrets.yaml -n api-servers'
    }
    
    stage('create K8s deployment')
    {
        sh '/usr/local/bin/kubectl apply -f deployment.yaml -n api-servers'
    }
    
    stage('create K8s service')
    {
        sh '/usr/local/bin/kubectl apply -f service.yaml -n api-servers'
    }
    
    stage('create K8s hpa')
    {
        sh '/usr/local/bin/kubectl apply -f hpa.yaml -n api-servers'
    }
}
