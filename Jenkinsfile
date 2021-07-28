pipeline {
    agent any
    stages {
        stage('Build Application') {
            steps {
				//sh 'mvn clean package' if pom.xml is available in root direcotry. In my app, inside devops java-tomcat-sample application is there
                sh 'mvn -f hello-world-war/pom.xml clean package'
            }
            post {
                success {
                    echo "Now Archiving the Artifacts...."
                    archiveArtifacts artifacts: '**/*.war'
                }
            }
        }
        stage('Deploy in Staging Environment'){
            steps{
                build job: 'Deploy_Application_Staging_Env'

            }
            
        }
       /* stage('Deploy to Production'){
            steps{
                timeout(time:5, unit:'DAYS'){
                    input message:'Approve PRODUCTION Deployment?'
                }
                build job: 'Deploy_Application_Prod_Env'
            }
        }
		*/
    }
}