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
			    for (String i : subfolders) {
				print i
                if(changeset pattern: "test1/*"){
                    echo 'change in test1'

                }if(changeset pattern: "test2/*"){
                    echo 'change in test2'

                }if(changeset pattern: "test3/*"){
                    echo 'change in test3'

                }
			    }
			}
		}
        }

    }


}
