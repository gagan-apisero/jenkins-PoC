pipeline {
  agent any
  environment {
			//App-name 
			APP_NAME = 'API'
	  		APP = "API-${timeStamp}"
			
	}
    stages{
        stage('list dir'){
		steps {
			script{
			    def subfolders = bat(script: '@dir /B /AD | @findstr /L /V "tmp" | @findstr /L /V ".git"', returnStdout: true).split(/\n\r/)
			    for (String i : subfolders) {
				print i
                stage('get changes') {
                when { changeset "${i}/*"}
                steps {
                    echo 'change happened'
                }
			    }
			}
		}
        }

    }


}
