pipeline {

  agent any

  stages{

    stage('Checkout Source') {
      steps {
        git url : 'https:/github.com/subhani314/myweb.git', branch:'master'
      }
    }

      stage("Build image"0
            steps {
              
                script {
                    const app = docker.build("subhani314/'helloworld:${env.BUILD
                }
            }
       }  

     stage("Push image") {
           steps {
              script {
                  docker.withRegistry('https://registry.hub.docker.com', 'dockerhub') {
                          constapp.push("latest")
                          constapp.push("${env.BUILD_id}")
                  }
              }
          }
       }


    stage('Deploy App') {
      steps {
        script {
          kubernetesDeploy(configs: "helloworld.yml", kubeconfigId: "mykubeconfig")
        }
      }
    }

  }

}
