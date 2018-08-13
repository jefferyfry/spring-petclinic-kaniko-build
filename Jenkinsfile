
pipeline {
  agent {
    kubernetes {
        label 'kaniko-build-pod'
        yamlFile 'podTemplate/spring-petclinic-kaniko-build.yaml'
    }
  }
  stages {
    stage('Maven Install') {
      steps {
        container('maven') {
          sh 'mvn clean install'
        }
      }
    }
    stage('Kaniko Build and Push') {
      steps {
        container(name:'kaniko', shell:'/busybox/sh') {
          sh '''#!/busybox/sh 
          /kaniko/executor -f `pwd`/Dockerfile -c `pwd` --destination gcr.io/cloudbees-public/spring-petclinic:latest
          '''
        } 
      }
    }
    stage('Deploy to Staging') {
      steps {
        echo 'deploy'
      }
    }
  }
}