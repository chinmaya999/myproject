pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }
        stage('Verify JAR') {
            steps {
                sh 'ls -l target/sample-app-1.0-SNAPSHOT.jar'
            }
        }
        stage('Deploy') {
            steps {
                sh '''
                pkill -f sample-app-1.0-SNAPSHOT.jar || true
                nohup java -jar target/sample-app-1.0-SNAPSHOT.jar > app.log 2>&1 &
                '''
            }
        }
    }
}

