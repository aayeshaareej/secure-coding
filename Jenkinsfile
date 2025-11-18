flag = true

pipeline {
    agent any

    parameters {
        // Types of parameters
        string(name: 'VERSION', defaultValue: '', description: 'version to deploy on prod')
        choice(name: 'VERSION_CHOICE', choices: ['1.1.0', '1.2.0', '1.3.0'], description: 'Choose version')
        booleanParam(name: 'executeTests', defaultValue: true, description: 'Run Test Stage?')
    }

    environment {
        // Variables usable by any stage
        NEW_VERSION = '1.3.0'
    }

    stages {

        stage('build') {
            steps {
                echo 'Building Project'
                echo "Selected VERSION: ${params.VERSION}"
                echo "Selected VERSION_CHOICE: ${params.VERSION_CHOICE}"
                echo "Env NEW_VERSION: ${NEW_VERSION}"
            }
        }

        stage('test') {
            when {
                expression {
                    params.executeTests   // test stage runs only if true
                }
            }
            steps {
                echo 'Testing Project'
            }
        }

    }
}
