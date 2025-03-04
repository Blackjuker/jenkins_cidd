pipeline{
    agent{
        docker{
            image "postman/newman"
            args '--entrypoint=""'
        }
    }
    triggers {
         upstream(upstreamProjects: 'prof_pipeline', threshold: hudson.model.Result.SUCCESS)
      }

    stages{
        stage('verifier la version de newman'){
            steps{
                sh "newman --version"
                   }
        }
        stage('test api'){
            steps{
                sh 'newman run collections/test_login.postman_collection.json -r cli,junit --reporter-junit-export="newman-report.xml"'
            }
        }
    }
    post{
        always{
            junit 'newman-report.xml'
        }
    }
}