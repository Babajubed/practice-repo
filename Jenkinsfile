pipeline {
    agent any
    parameters {
        choice(
            name: 'environment',
            choices: ['PRE', 'PRO'],
            description: 'Run Flyway database migration using the latest master branch from prices in what environment?'
        )
    }
    stages {
        stage('Wat') {
            steps {
                echo "Selected environment: ${params.environment}"
            }
        }
    }
}
