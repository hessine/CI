pipeline {
    agent {
        label "master"
    }
   
    environment {
        // This can be nexus3 or nexus2
        NEXUS_VERSION = "nexus3"
        // This can be http or https
        NEXUS_PROTOCOL = "http"
        // Where your Nexus is running
        NEXUS_URL = "1localhost:8081"
        // Repository where we will upload the artifact
        NEXUS_REPOSITORY = "Releases"
        // Jenkins credential id to authenticate to Nexus OSS
        NEXUS_CREDENTIAL_ID = "admin:admin123"
    }
    stages {
        stage("clone code") {
            steps {
                script {
                    // Let's clone the source
                    git 'https://github.com/hessine/CI.git';
                }
            }
        }
        stage("mvn build") {
            steps {
                script {
                    // If you are using Windows then you should use "bat" step
                    // Since unit testing is out of the scope we skip them
                    bat "mvn package -DskipTests=true"
                }
            }
        }
        stage("mvn clean install ") {
            steps {
                script {
                    // If you are using Windows then you should use "bat" step
                    // Since unit testing is out of the scope we skip them
                    bat "mvn clean"
                }
            }
        }
        stage("mvn test ") {
            steps {
                script {
                    // If you are using Windows then you should use "bat" step
                    // Since unit testing is out of the scope we skip them
                    bat "mvn test"
                }
            }
        }
     
        
        
           
         stage("mvn deploy") {
            steps {
                script {
                    // If you are using Windows then you should use "bat" step
                    // Since unit testing is out of the scope we skip them
                    bat "C:\\CI\\apache-maven-3.6.2\\bin\\mvn deploy"
                }
            }
        }
        stage("mail") {
          steps {
          mail bcc: '', body: '''Hello User the build of your project successed.
            Jenkins.''', cc: '', from: '', replyTo: '', subject: 'Build succed', to: 'chebbi.hessine@gmail.com'
          }
        
        }
        
        
       
}


}
