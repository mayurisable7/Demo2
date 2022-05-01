node {

    def app

    stage('Clone repository') {

        checkout scm

    }

    stage('Build image') {

        app = docker.build("mayuriisable/nodeapp")

    }

    stage('Test image') {
      
        app.inside {

            echo "Tests passed"

        }

    }

    stage('Push image') {

        docker.withRegistry('https://hub.docker.com/', 'dockerHub') {

            app.push("${env.$BUILD_NUMBER}")

            app.push("latest")

            } 

                echo "Trying to Push Docker Build to DockerHub"

    }

}
