pipeline {
    agent any

    parameters {
        booleanParam(name: "RUN_INTEGRATION_TESTS", defaultValue: true)
    }

    stages {
        stage('Test'){
            parallel {
                stage('Unit tests'){
                    steps{
                        sh './mvnw test -D testGroup=unit'
                    }
                }
            }
        }

        stage('Build'){
            steps{
                script{
                    try {
                        sh './mvnw package -D skipTests'
                    } catch (ex) {
                        echo "Error while generating JAR file"
                        throw ex
                    }
                }
            }
        }
    }
}