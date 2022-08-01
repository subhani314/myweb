pipeline {
    agent any
    tools {
        maven 'Maven-3.6.1'
    }
    
    environment{
        PATH = "/opt/maven3/bin:$PATH"
    }

  stages{

    stage('Checkout Source') {
      steps {
        git url : 'https:/github.com/subhani314/myweb.git', branch:'master'
      }
    }
     stage("Maven Build"){
            steps{
                sh "mvn clean sonar:sonar package"
                
            }
        }
         stage('Upload jar To Nexus'){
            steps{
             nexusArtifactUploader artifacts: [
                       [
                            artifactId: 'myweb', 
                            classifier: '', 
                            file: "target/myweb-8.2.0.jar", 
                            type: 'jar'
                       ]
                  ], 
                   credentialsId: 'nexus3', 
                  groupId: 'in.javahome', 
                  nexusUrl: '35.78.88.135:8081', 
                  nexusVersion: 'nexus3', 
                  protocol: 'http', 
                  repository: 'sample-releases', 
                  version: '8.2.0'  
              }
            }

      stage('Build Docker image'){
            steps {
              
                script {
                    app = docker.build("subhani314/'helloworld:${env.BUILD
                    FROM node:14

                    WORKDIR/usr/src/app

                    COPY package*.json app.js./

                    RUN npm install

                    EXPOSE 3000

                    CMD["node",app.js"]
                }
            }
       }  

      stage('Push Docker Image'){
             steps{
                  withCredentials([string(credentialsId: 'DOCKER_HUB_CREDENTIALS', variable: 'DOCKER_HUB_CREDENTIALS')]) {
                      sh "docker login -u deepikac2021 -p ${DOCKER_HUB_CREDENTIALS}"
             }
            sh 'docker push subhani314/spring-boot-mongo'
        }
      }

stage("Deploy To Kuberates Cluster"){
              steps{
                   kubernetesDeploy(
                   configs: 'helloworld.yml', 
                   kubeconfigId: 'KUBERNETES_CLUSTER_CONFIG',
                   enableConfigSubstitution: true
            )
        }
    }
        
    }
}
   
