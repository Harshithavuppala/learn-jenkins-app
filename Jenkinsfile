pipeline {
    agent any

    stages {
        
        stage('Hello') {
            agent {
                docker {
                    image 'node:18-alpine'
                    reuseNode true
                }
            }
            steps {
                sh '''
                    ls -la
                    node --version
                    npm --version
                    npm ci
                    npm run build
                '''
            }
        }
        stage('test') {
            agent {
                docker {
                    image 'node:18-alpine'
                    reuseNode true
                }
            }
            steps{
                sh '''
                echo Test stage
                test -f build/index.html
                echo $?
                npm test
            '''
            }
          
        }
    }
}
