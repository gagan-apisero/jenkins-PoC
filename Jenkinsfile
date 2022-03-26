// backup dynamic jenkins file
def timeStamp = Calendar.getInstance().getTime().format('YYYYMMdd-hhmmss',TimeZone.getTimeZone('IST'))
def changedFiles=[]
pipeline {
  agent any
  environment {
			//App-name 
			APP_NAME = 'API'
	  		APP = "API-${timeStamp}"
	}
    stages{
        stage('Pre Stage'){
            steps {
                echo 'checking folders'
				script{
					// def subfolders = bat(script: '@dir /B /AD | @findstr /L /V "tmp" | @findstr /L /V ".git"', returnStdout: true).split(/\n\r/)
					def changeLogSets = currentBuild.changeSets
                    for (int i = 0; i < changeLogSets.size(); i++) {
                        def entries = changeLogSets[i].items
                        for (int j = 0; j < entries.length; j++) {
                            def entry = entries[j]
                            // echo "${entry.commitId} by ${entry.author} on ${new Date(entry.timestamp)}: ${entry.msg}"
                            def files = new ArrayList(entry.affectedFiles)
                            for (int k = 0; k < files.size(); k++) {
                                def file = files[k]
                                // echo "  ${file.editType.name} ${file.path}"
                                changedFiles+=("${file.path}").split('/')[0]
                            }
                        }
                    }
		        }
            }
        }

        stage('Initialize'){
            environment {
                ANYPOINT_CREDENTIALS = credentials('anypoint.credentials')
                ANYPOINT_CLIENT_ID = credentials('client_id')
                ANYPOINT_CLIENT_SECRET = credentials('client_secret')
            }
            steps{
                echo 'Creating Stages for each change project folder'
                script{
                    changedFiles.remove("Jenkinsfile") // removing Jenkinsfile coz dont want a stage for Jenkinsfile
                    for(String i : changedFiles.unique()){
                        echo "${i}"
                        stage("Build ${i}") {
                                echo "Building ${i}"
                                dir("${i}"){
                                    bat "mvn clean package -Djar.name=${i}-%APP%"
                                }
			            }
                        stage("Deploying ${i}") {
                                echo "Deploying ${i}"
                                dir("${i}"){
                                    bat "mvn deploy -DskipTests -DmuleDeploy -Danypoint.username=%ANYPOINT_CREDENTIALS_USR% -Danypoint.password=%ANYPOINT_CREDENTIALS_PSW% -Danypoint.platform.client_id=%ANYPOINT_CLIENT_ID% -Danypoint.platform.client_secret=%ANYPOINT_CLIENT_SECRET% -Danypoint.env=Sandbox -Danypoint.region=us-east-1 -Danypoint.workers=1 -Danypoint.name=${i}-api -Djar.name=${i}-%APP% -Dmule.artifact=%WORKSPACE%\\${i}\\target\\${i}-%APP%-mule-application.jar"
                                }
			            }
                    }
                }
            }
        }

    }


}
