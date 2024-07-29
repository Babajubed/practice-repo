pipeline {
    agent any
    stages {
        stage('usernamePassword') {
            steps {
                script {
                    withCredentials([
                        usernamePassword(credentialsId: 'github-username-password',
                                         usernameVariable: 'USERNAME',
                                         passwordVariable: 'PASSWORD')
                    ]) {
                        echo 'USERNAME=' + env.USERNAME
                        echo 'PASSWORD=' + env.PASSWORD
                        // Avoid printing sensitive data directly in real scenarios
                    }
                }
            }
        }
        stage('usernameColonPassword') {
            steps {
                script {
                    withCredentials([
                        usernameColonPassword(
                            credentialsId: 'github-username-colon-password',
                            variable: 'USERPASS')
                    ]) {
                        echo 'USERPASS=' + env.USERPASS
                        // Avoid printing sensitive data directly in real scenarios
                    }
                }
            }
        }
        stage('string (secret text)') {
            steps {
                script {
                    withCredentials([
                        string(
                            credentialsId: 'github-token',
                            variable: 'GITHUB_TOKEN')
                    ]) {
                        echo 'GITHUB_TOKEN=' + env.GITHUB_TOKEN
                        // Avoid printing sensitive data directly in real scenarios
                    }
                }
            }
        }
        stage('sshUserPrivateKey') {
            steps {
                script {
                    withCredentials([
                        sshUserPrivateKey(
                            credentialsId: 'github-ssh-key',
                            keyFileVariable: 'KEY_FILE',
                            passphraseVariable: 'PASSPHRASE',
                            usernameVariable: 'USERNAME')
                    ]) {
                        echo 'KEY_FILE=' + env.KEY_FILE
                        echo 'PASSPHRASE=' + env.PASSPHRASE
                        echo 'USERNAME=' + env.USERNAME
                        echo 'KEY_FILE Content=' + readFile(env.KEY_FILE)
                        // Avoid printing sensitive data directly in real scenarios
                    }
                }
            }
        }
        stage('dockerCert') {
            steps {
                script {
                    withCredentials([
                        dockerCert(
                            credentialsId: 'docker-cert',
                            variable: 'DOCKER_CERT_PATH')
                    ]) {
                        echo 'DOCKER_CERT_PATH=' + env.DOCKER_CERT_PATH
                        echo 'DOCKER_CERT_PATH/ca.pem=' + readFile("${env.DOCKER_CERT_PATH}/ca.pem")
                        echo 'DOCKER_CERT_PATH/cert.pem=' + readFile("${env.DOCKER_CERT_PATH}/cert.pem")
                        echo 'DOCKER_CERT_PATH/key.pem=' + readFile("${env.DOCKER_CERT_PATH}/key.pem")
                        // Avoid printing sensitive data directly in real scenarios
                    }
                }
            }
        }
        stage('list credentials ids') {
            steps {
                script {
                    // List credentials IDs (use for debugging purposes only)
                    sh 'cat $JENKINS_HOME/credentials.xml | grep "<id>"'
                }
            }
        }
    }
}
