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
    }
}