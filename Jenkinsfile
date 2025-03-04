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
                sh 'newman run test_login.postman_collection -e tes_login.postman_collection '
               // echo "bonjour"
            }
        }
    }
    // post{
    //     always{
    //         junit 'newman-report.xml'
    //     }
    // }
}