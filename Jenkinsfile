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
// 			    def changeSetIterator = changeSet.iterator()
				def data = {changeset pattern: "test1/*"}
				print data
				if( data == true){
				echo 'hello true'
				}
// 				while(changeSetIterator.hasNext()){
// 					def gitChangeSet = changeSetIterator.next()
// 					for(String path:gitChangeSet.getPaths()){
// 						print path.getPath() 
// 					}
// 				}
				print changeSet
			    for (changeLogSet : changeSet) {
				    for(entry:changeLogSet.getItems()){
					    for(file : entry.getAffectedFiles()){
						    if(file.getPath() ==~ /^test1/){
						    echo 'change under test1'
						    }
					    }
				    }
				
			    }
			}
		}
        }

    }


}
