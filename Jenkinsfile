pipeline {
    agent any
    environment {
        DISABLE_AUTH = 'true'
        DB_ENGINE = 'sqlite'
        AWS_ACCESS_KEY_ID = credentials('jenkins-aws-secret-key-id')
        AWS_SECRET_ACCESS_KEY = credentials('jenkins-aws-secret-access-key')
    }

    stages {
        stage('Build') {
            steps {
                sh 'printenv'
                echo "Database engine is ${DB_ENGINE}"
                echo "DISABLE_AUTH is ${DISABLE_AUTH}"
                echo "AWS_ACCESS_KEY_ID is ${AWS_ACCESS_KEY_ID}"
                echo "AWS_SECRET_ACCESS_KEY is ${AWS_SECRET_ACCESS_KEY}"
            }
        }
    }
}
