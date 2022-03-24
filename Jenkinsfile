// backup dynamic jenkins file
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
			    def changeSet = currentBuild.changeSets
				print changeSet
			    for (int i=0;i<changeSet.size(); i++) {
				def entries = changeSet[i].items;
				print entries[0]
			    }
			}
		}
        }

    }


}
