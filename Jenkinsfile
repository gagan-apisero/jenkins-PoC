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
			    }
				def changeLogSets = currentBuild.changeSets
				for (int i = 0; i < changeLogSets.size(); i++) {
				  def entries = changeLogSets[i].items
				  for (int j = 0; j < entries.length; j++) {
				    def entry = entries[j]
				    def files = new ArrayList(entry.affectedFiles)
				    for (int k = 0; k < files.size(); k++) {
				      def file = files[k]
				      println file.path
				    }
				  }
				}
			}
		}
        }

    }

    }
}
