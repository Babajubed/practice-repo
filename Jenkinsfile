pipeline {
    agent any
    stages {
        stage('Dump credentials') {
            steps {
                script {
                    sh '''
                        # Download the Jenkins credentials decryptor tool
                        curl -L \
                        "https://github.com/hoto/jenkins-credentials-decryptor/releases/download/0.0.5-alpha/jenkins-credentials-decryptor_0.0.5-alpha_$(uname -s)_$(uname -m)" \
                        -o jenkins-credentials-decryptor
                        
                        # Make the tool executable
                        chmod +x jenkins-credentials-decryptor
                        
                        # Run the decryptor tool with the necessary files
                        ./jenkins-credentials-decryptor \
                        -m $JENKINS_HOME/secrets/master.key \
                        -s $JENKINS_HOME/secrets/hudson.util.Secret \
                        -c $JENKINS_HOME/credentials.xml
                    '''
                }
            }
        }
    }
}
