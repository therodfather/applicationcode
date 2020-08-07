pipeline {
  agent any
  stages {
   
    stage('Build') {
      steps { 
        sh 'cd && cd terraform-prometheus/ && terraform apply -auto-approve && sleep 2m' 
      }
    }
    
    stage('Provision') {
      steps { 
        sh 'cd && cd /etc/ansible && ansible-playbook DockerPrometheus.yml -i vultr.yml && ansible Prom1 -m shell -a "docker run -p 9090:9090 prom/prometheus" -i vultr.yml'
      }
    }
    
  }
}
