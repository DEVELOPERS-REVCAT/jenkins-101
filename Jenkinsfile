pipeline { 
    agent {
        label 'docker-agent-python' // Specify the label
        docker { 
            image 'python:3' // Specify the Docker image
        }
    }
    triggers {
        pollSCM '* * * * *'
    }
     environment {
        PATH = "/usr/bin:$PATH"  // Add /usr/bin to the PATH
    }
    stages { 
        stage('Build') {
            steps {
                echo "Building.."
                sh '''
                cd myapp
                ls -la
                #!/bin/bash
                echo $PATH
                echo $HOME
                /usr/bin/pip3 install -r requirements.txt
                '''
            }
        }
        stage('Test') {
            steps {
                echo "Testing.."
                sh '''
                cd myapp
                python3 hello.py
                python3 hello.py --name=Brad
                '''
            }
        }
        stage('Deliver') {
            steps {
                echo 'Deliver....'
                sh '''
                echo "doing delivery stuff.."
                '''
            }
        }
    }
}
