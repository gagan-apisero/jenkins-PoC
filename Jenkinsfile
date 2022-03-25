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
			    def changeSet = build.changeSets
			    def changeSetIterator = changeSet.iterator()
				while(changeSetIterator.hasNext()){
					final gitChangeSet = changeSetIterator.next()
					for(final path:gitChangeSet.getPaths()){
						print path.getPath()
					}
				}
				print changeSet
			    for (int i=0;i<changeSet.size(); i++) {
				def entries = changeSet[i].items;
					def entry = entries[0];
				    	print entries
				    	print entry
			    }
			}
		}
        }

    }


}
