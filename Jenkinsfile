pipeline { 
    agent { label 'master' }
    options {
        skipStagesAfterUnstable()
    }
    stages {
        stage('Build') { 
            steps { 
                sh 'mvn -B -DskipTests clean package' 
            }
        }
        stage('Test'){
            steps {
                sh 'mvn test'
            }
            post {
                success {
                    junit 'target/surefire-reports/*.xml'
                }
            }
        }
        stage('Run') {
            steps {
                sh 'make publish'
            }
        }
    }
}
