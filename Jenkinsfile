pipeline {
    agent any
    environment {
        DB_ENGINE = 'sqlite'
        AWS_ACCESS_KEY_ID = credentials('jenkins-aws-secret-key-id')
        AWS_SECRET_ACCESS_KEY = credentials('jenkins-aws-secret-access-key')
        BITBUCKET_COMMON_CREDS = credentials('jenkins-bitbucket-common-creds')
    }

    stages {
        stage('Build') {
            steps {
                sh 'printenv'
                echo "DB_ENGINE is ${DB_ENGINE}"
                echo "AWS_ACCESS_KEY_ID is ${AWS_ACCESS_KEY_ID}"
                echo "AWS_SECRET_ACCESS_KEY is ${AWS_SECRET_ACCESS_KEY}"
                echo "BITBUCKET user is ${BITBUCKET_COMMON_CREDS_USR}, BITBUCKET password is ${BITBUCKET_COMMON_CREDS_PSW}"
            }
        }
    }
}
