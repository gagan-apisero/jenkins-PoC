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
			    dirsl = readDir()
			    def size = dirsl.size()
			    print size
			    for (String i : dirsl) {
				print i
			    }
			}
		}
        }

    }


}
