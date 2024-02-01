pipeline{
    agent any
    //can add environment and tool like below and later can bind their value in steps
    tools{
        maven "maven"
    }
    stages{

        stage("mvn clean install"){
            steps{
                bat "mvn clean install"
            }
        }
        stage("deploy adapters"){
             steps {
                 script {
                    def tomcatUrl = 'http://localhost:8081'
                    def warFile = findFiles(glob: '**/*.war')[0]

            bat "curl -v --user root:root --upload-file ${warFile} ${tomcatUrl}"
        }
              //   bat "deploy adapters: [tomcat9(credentialsId: '7c73983f-aa98-4e9a-9cfb-c4d69821794f', path: '', url: 'http://localhost:8081/')], contextPath: null, war: '**/*.war'"
           }

        }
    }
    //can add some comments after deploying project successfully on jenkins in post
    post{
        always{
            echo "always will print a message always either its fail or success"

        }
        success{
            echo "success msg will print in case of successfully deployed"

        }
        failure{
            echo  "failure msg will print in case of project is not deployed"
        }
    }
}
