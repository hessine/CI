pipeline {
    agent {
        label "master"
    }
   
    environment {
        // This can be nexus3 or nexus2
        NEXUS_VERSION = "nexus3"
        // This can be http or https
        NEXUS_PROTOCOL = "http"
  
        NEXUS_URL = "1localhost:8081"
     
        NEXUS_REPOSITORY = "Releases"
     
        NEXUS_CREDENTIAL_ID = "admin:admin123"
    }
    stages {
        stage("clone code") {
            steps {
                script {
              
                    git 'https://github.com/hessine/CI.git';
                }
            }
        }
        stage("mvn build") {
            steps {
                script {
         
               
                    bat "mvn package -DskipTests=true"
                }
            }
        }
        stage("mvn clean install ") {
            steps {
                script {
               
                    bat "mvn clean"
                }
            }
        }
        stage("mvn test ") {
            steps {
                script {
                 
                    bat "mvn test"
                }
            }
        }
     
        
        
           
         stage("mvn deploy") {
            steps {
                script {
                  
                    bat "C:\\CI\\apache-maven-3.6.2\\bin\\mvn deploy"
                }
            }
        }
       
        
        
       
}


}
