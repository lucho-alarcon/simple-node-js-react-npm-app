pipeline {
    agent any
    environment {
        CI = 'true'
    }
    stages {
        stage('Build FirstName') {
            steps {
                echo 'Lucho'
            }
        }
        stage('Build LastName') {
            steps {
                echo 'Alarcon'
            }
        }
   }
}


pipeline {

  agent any

  tools {
    nodejs "node16170"
  }

  parameters {
    string(name: 'container_name', defaultValue: 'pagina_web', description: 'Nombre del contenedor de docker.')
    string(name: 'image_name', defaultValue: 'pagina_img', description: 'Nombre de la imagene docker.')
    string(name: 'tag_image', defaultValue: 'lts', description: 'Tag de la imagen de la página.')
    string(name: 'container_port', defaultValue: '80', description: 'Puerto que usa el contenedor')
  }

  stages {

    stage('install') {
      steps {
        git branch: 'master', url: 'https://github.com/lucho-alarcon/simple-node-js-react-npm-app.git'
        sh 'npm install' 
      }
    }

    stage('test') {
      steps {
        sh 'npm run test'
      }
    }

    stage('build') {
      steps {
         echo 'build here!'
        // dir('frontend') {
        //   script {
        //     try {
        //       sh 'docker stop ${container_name}'
        //       sh 'docker rm ${container_name}'
        //       sh 'docker rmi ${image_name}:${tag_image}'
        //     } catch (Exception e) {
        //       echo 'Exception occurred: ' + e.toString()
        //     }
        //   }
        //   sh 'npm run build'
        //   sh 'docker build -t ${image_name}:${tag_image} .'
        // }
      }
    }

    stage('deploy') {

      steps {
        echo 'deploy here!'
        // sh 'docker run -d -p ${container_port}:80 --name ${container_name} ${image_name}:${tag_image}'
      }

    }
  }

}

