// backup static jenkins file
def timeStamp = Calendar.getInstance().getTime().format('YYYYMMdd-hhmmss',TimeZone.getTimeZone('IST'))
pipeline {
  agent any
  environment {
			//App-name 
			APP_NAME = 'API'
	  		APP = "API-${timeStamp}"
			
	}
    stages{
        stage('Initialize'){
            steps {
                echo 'checking folders'
				script{
					def subfolders = bat(script: '@dir /B /AD | @findstr /L /V "tmp" | @findstr /L /V ".git"', returnStdout: true).split(/\n\r/)
					for (String i : subfolders) {
						stage ("Build ${i}") {
							when { changeset pattern: "${i}/*" }
							steps{
								echo "Building ${i}"
								dir("${i}"){
								bat "mvn clean package -Djar.name=${i}-%APP%"
								}
							}
						}
					}
				}
            }
        }

    }


}
