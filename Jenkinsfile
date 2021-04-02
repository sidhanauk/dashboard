// Uses Declarative syntax to run commands inside a container.
pipeline {
    agent {
        kubernetes {
            yaml '''
apiVersion: v1
kind: Pod
spec:
  containers:
  - name: helm
    image: alpine/helm
    command:
    - sleep
    args:
    - infinity
  - name: shell
    image: ubuntu
    command:
    - sleep
    args:
    - infinity
'''
            defaultContainer 'shell'
        }
    }
    stages {
        stage('Main') {
            steps{
            container('shell'){
                //sh 'cat charts.json'
                
                def chartVars = readJSON file: "${WORKSPACE}/charts.json"
                
                script {
                    print(chartVars)
                }
            }
        }
    }
  }
}
