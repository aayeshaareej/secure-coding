def flag = true   // you can change this dynamically later

pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building Project'
            }
        }

        stage('Test') {
            when {
                expression {
                    flag == false     // ❗ only runs Test stage if flag is false
                }
            }
            steps {
                echo 'Testing Project'
            }
        }

        stage('Deploy') {
            when {
                expression {
                    flag == true      // ❗ only runs Deploy stage if flag is true
                }
            }
            steps {
                echo 'Deploying Project'
            }
        }
    }

    post {
        always {
            echo 'Post build condition running'
        }
        failure {
            echo 'Post Action if build Failed'
        }
    }
}
