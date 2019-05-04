pipeline {
    agent any
    stages {
        stage('Ansible Role Deploy HAProxy') {
            parallel {
                stage('Pylint') {
                    agent {
                        docker {
                            image 'dsgnr/base-python3.7-alpine-docker'
                        }
                    }
                    stages {
                        stage('Setup') {
                            steps {
                                echo "Installing requirements..."
                                sh '''pip3 install -q -U pip
                                      pip3 install -r requirements.txt'''
                            }
                        }
                        stage('Molecule') {
                            steps {
                                echo "Running Molecule..."
                                sh 'molecule test > molecule.log'
                            }
                        }
                    }
                    post {
                        always {
                            recordIssues enabledForFailure: true, tool: molecule(id: 'ansible-molecule', name: 'Molecule', pattern: 'molecule.log', reportEncoding: 'UTF-8')
                        }
                        failure {
                            sh 'cat molecule.log'
                        }
                    }
                }
            }
        }

    }
    post {
        always {
            deleteDir()
        }
    }
}
