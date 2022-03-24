pipeline {
  agent any
  environment {
			//App-name 
			APP_NAME = 'API'
	  		APP = "API-${timeStamp}"
			
	}
    stages{
        stage('App test1'){
		steps {
			script{
			    def subfolders = bat(script: '@dir /B |findstr /L /V "temp" |findstr /L /V ".git"', returnStdout: true).split(/\n\r/)
			    for (String i : subfolders) {
				print i
			    }
			}
		}
        }

    }


}
