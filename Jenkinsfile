pipeline {
    agent {
        // how the pipeline will be built
        docker{
                image 'adoptopenjdk/openjdk11:jdk-11.0.3_7'
                args '--network ci --mount type=volume,source=ci-maven-home,target=/root/.m2'
                }
        }
    }

    environment {
        // properties or environment variables, new or derived
        ORG_NAME="deors"
        APP_NAME = "workshop-pipelines"
        APP_CONTEXT_ROOT= "/"
        APP_LISTENING_PORT= "8080"
        TEST_CONTAINER_NAME="ci_$(APP_NAME)-$(BUILD-NUMBER)"
        DOCKER_HUB= credentials("${ORG_NAME}-docker-hub")
    }

    stages {
        stage('Compile') {
            steps {
                echo "-=- compiling project -=-"
                sh "./mvnw clean compile"
            }
        }

        ...

        stage('stage-n-name') {
            steps {
                // steps for stage n come here
            }
        }
    }

    post {
        // post-process activities, e.g. cleanup or publish
    }
}