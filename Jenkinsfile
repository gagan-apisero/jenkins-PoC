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
// 				while(changeSetIterator.hasNext()){
// 					def gitChangeSet = changeSetIterator.next()
// 					for(String path:gitChangeSet.getPaths()){
// 						print path.getPath() 
// 					}
// 				}
				print changeSet
			    for (changeLogSet in changeSet) {
				    for(entry in changeLogSet.getItems()){
					    for(file in entry.getAffectedFiles()){
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
