pipeline {
   agent { label 'king' }
     // agent any
    tools {
        jdk 'JDK17'
       
        maven 'Maven'
    }

   stages {

        stage('Checkout') {
            steps {
                git branch: 'feature-1', url: 'https://github.com/kavithakavi9493/bus_booking.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean package -DskipTests=false'
            }
        }

        stage('Archive Artifact') {
            steps {
                archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
            }
        }

        stage('Run Application') {
            steps {
                  sh 'mvn spring-boot:run'
                  dir('/var/lib/jenkins/workspace/bus_booking_feature-1/target') {
                   sh """
                     //   nohup java -jar simple-parcel-service-app-1.0-SNAPSHOT.jar > app.log 2>&1 &
                        //echo "Application started"
                   """
                   
                }
            }
        }
    }
}
