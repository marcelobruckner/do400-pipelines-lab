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

                stage('Integration tests'){
                    when {
                        espression { return params.RUN_INTEGRATION_TESTS }
                    }

                    steps{
                        sh './mvnw test -D testGroups=integration'
                    }
                }
            }
        }
    }
}