pipeline {
   agent none

   stages {

        stage('app test') {
            when {
                branch 'feature-*'
                //     changeset '**/app/**'
            }
            agent any

            steps {
                echo 'testing python App'
                dir('app/tests'){
                    // The AUTH_TOKEN and PROJECT should be set from your Jenkins setup
                    sh 'export GIT_BRANCH'
                    sh 'export AUTH_TOKEN'
                    sh 'export PROJECT'
                    sh 'bash ./bunnycli.sh'
                }
            }
        }

        stage('app env') {
            agent any

            steps {
                echo 'printing env for App'
                dir('app'){
                    sh 'env'
                    sh 'echo $GIT_BRANCH'
                }
            }
        }

    }
    post {
        always {
            echo 'Pipeline finished executing'
        }
    }
}
