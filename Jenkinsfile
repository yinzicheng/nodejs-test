pipeline {
    agent any
    environment {
        DB_ENGINE = 'sqlite'
        AWS_ACCESS_KEY_ID = credentials('jenkins-aws-secret-key-id')
        AWS_SECRET_ACCESS_KEY = credentials('jenkins-aws-secret-access-key')
    }
    parameters {
        string(name: 'Greeting', defaultValue: 'Hello', description: 'How should I greet the world?')
    }

    stages {
        stage('Build') {
            when {
                branch 'master'
            }
            steps {
                withCredentials([usernamePassword(credentialsId: 'jenkins-bitbucket-common-creds', usernameVariable: 'USERNAME', passwordVariable: 'USERPASS')]) {
                    sh 'printenv'
                    echo "DB_ENGINE is ${DB_ENGINE}"
                    echo "AWS_ACCESS_KEY_ID is ${AWS_ACCESS_KEY_ID}"
                    echo "AWS_SECRET_ACCESS_KEY is ${AWS_SECRET_ACCESS_KEY}"
                    echo "BITBUCKET user is ${USERNAME}, BITBUCKET password is ${USERPASS}"
                    echo "Greeting: ${params.Greeting} yinzicheng"
                }
            }
        }

//        stage('Deploy - Staging') {
//            steps {
//                echo 'Deploy - Staging'
//            }
//        }
//
//        stage('Sanity check') {
//            steps {
//                input 'Does the staging environment look ok?'
//            }
//        }
//
//        stage('Deploy - Production') {
//            steps {
//                echo 'Deploy - Production'
//            }
//        }
    }

//    post {
//        always {
//            archiveArtifacts artifacts: 'build/libs/**/*.jar', fingerprint: true
//        }
//        failure {
//            mail to: 'team@example.com',
//                    subject: 'Failed Pipeline: ${currentBuild.fullDisplayName}',
//                    body: 'Something is wrong with ${env.BUILD_URL}'
//        }
//    }
}
