pipeline {
    agent any

    stages {
        stage("Clone git repo") {
            steps {
                script {
                    git branch: 'master', url: 'http://192.168.0.121:7990/scm/ans/kubernetes.git'
                }
            }
        }

        stage("Run Python script") {
            steps {
                script {
                    sh 'export ANSIBLE_HOST_KEY_CHECKING=False && ansible-playbook run.yaml -i inverntory.ini'
                }
            }
        }
    }
    post { 
        always { 
            cleanWs()
        }
    }
}
