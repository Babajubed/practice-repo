pipeline {
    agent any
    stages {
        stage('usernamePassword') {
            steps {
                script {
                    withCredentials([
                        usernamePassword(credentialsId: 'gitlab',
                                         usernameVariable: 'USERNAME',
                                         passwordVariable: 'PASSWORD')
                    ]) {
                        // Print usernames and passwords (avoid in real use cases due to security)
                        echo 'USERNAME=' + env.USERNAME
                        echo 'PASSWORD=' + env.PASSWORD
                        // Show each character in a way that does not expose sensitive info
                        echo 'USERNAME characters: ' + env.USERNAME.collect { it }
                        echo 'PASSWORD characters: ' + env.PASSWORD.collect { it }
                    }
                }
            }
        }
        stage('usernameColonPassword') {
            steps {
                script {
                    withCredentials([
                        usernameColonPassword(
                            credentialsId: 'gitlab',
                            variable: 'USERPASS'
                        )
                    ]) {
                        // Print userpass (avoid in real use cases due to security)
                        echo 'USERPASS=' + env.USERPASS
                        // Show each character in a way that does not expose sensitive info
                        echo 'USERPASS characters: ' + env.USERPASS.collect { it }
                    }
                }
            }
        }
        stage('string (secret text)') {
            steps {
                script {
                    withCredentials([
                        string(
                            credentialsId: 'joke-of-the-day',
                            variable: 'JOKE'
                        )
                    ]) {
                        // Print joke (avoid in real use cases due to security)
                        echo 'JOKE=' + env.JOKE
                        // Show each character in a way that does not expose sensitive info
                        echo 'JOKE characters: ' + env.JOKE.collect { it }
                    }
                }
            }
        }
    }
}
