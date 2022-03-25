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
        stage('App test1'){
            steps {
                echo 'Building test1'
		    dir("test1"){
			bat 'mvn clean package -Djar.name=test1-%APP%'
		    }
		println(currentBuild.changeSets)
            }
        }

    }


}
