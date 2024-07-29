pipeline {
    agent any
    stages {
        stage('usernamePassword') {
            steps {
                script {
                    withCredentials([
                        usernamePassword(credentialsId: 'github',
                                         usernameVariable: 'USERNAME',
                                         passwordVariable: 'PASSWORD')
                    ]) {
                        echo 'USERNAME=' + env.USERNAME
                        echo 'PASSWORD=' + env.PASSWORD
                    }
                }
            }
        }
        stage('string (secret text)') {
            steps {
                script {
                    withCredentials([
                        string(
                            credentialsId: 'secret-text-id',
                            variable: 'SECRET'
                        )
                    ]) {
                        echo 'SECRET=' + env.SECRET
                    }
                }
            }
        }
    }
}
