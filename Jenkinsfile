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
		    script{
		def rc = bat(script: "git status -s ${dir} | grep -q ${dir}",returnStatus: true)
		  print rc
		 bat(script: "git status -s ${dir} | grep -q ${dir}")
		bat(script: "git --no-pager diff origin/${params.target} --name-only", returnStdout: true).split('\n')
		println(currentBuild.changeSets)
		    }
            }
        }

    }


}
