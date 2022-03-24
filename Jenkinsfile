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
            when { changeset pattern: "test1/*" }
            steps {
                echo 'Building test1'
		    dir("test1"){
			bat 'mvn clean package -Djar.name=test1-%APP%'
		    }
            }
        }
        stage('Depoly test1'){
            environment {
                ANYPOINT_CREDENTIALS = credentials('anypoint.credentials')
                ANYPOINT_CLIENT_ID = credentials('client_id')
                ANYPOINT_CLIENT_SECRET = credentials('client_secret')
            }
            when { changeset pattern: "test1/*" }
            steps{
                echo 'Depolying test1 app'
                dir("test1"){
                bat 'mvn deploy -DskipTests -DmuleDeploy -Danypoint.username=%ANYPOINT_CREDENTIALS_USR% -Danypoint.password=%ANYPOINT_CREDENTIALS_PSW% -Danypoint.platform.client_id=%ANYPOINT_CLIENT_ID% -Danypoint.platform.client_secret=%ANYPOINT_CLIENT_SECRET% -Danypoint.env=Sandbox -Danypoint.region=us-east-1 -Danypoint.workers=1 -Danypoint.name=test1-api -Djar.name=test1-%APP% -Dmule.artifact=%WORKSPACE%\\test1\\target\\test1-%APP%-mule-application.jar'
                }
            }
        }
        stage('App test2'){
            when { changeset pattern: "test2/**" }
            steps {
                echo 'Building test2'
                dir("test2"){
                bat 'mvn clean package -Djar.name=test2-%APP%'
                }
            }
        }
        stage('Depoly test2'){
            environment {
                ANYPOINT_CREDENTIALS = credentials('anypoint.credentials')
                ANYPOINT_CLIENT_ID = credentials('client_id')
                ANYPOINT_CLIENT_SECRET = credentials('client_secret')
            }
            when { changeset pattern: "test2/*" }
            steps{
                echo 'Depolying test2 app'
                dir("test2"){
                bat 'mvn deploy -DskipTests -DmuleDeploy -Danypoint.username=%ANYPOINT_CREDENTIALS_USR% -Danypoint.password=%ANYPOINT_CREDENTIALS_PSW% -Danypoint.platform.client_id=%ANYPOINT_CLIENT_ID% -Danypoint.platform.client_secret=%ANYPOINT_CLIENT_SECRET% -Danypoint.env=Sandbox -Danypoint.region=us-east-1 -Danypoint.workers=1 -Danypoint.name=test2-api -Djar.name=test2-%APP% -Dmule.artifact=%WORKSPACE%\\test2\\target\\test2-%APP%-mule-application.jar'
                }
            }
        }
        stage('App test3'){
            when { changeset pattern: "test3/*" }
            steps {
                echo 'Building test3'
                dir("test3"){
                bat 'mvn clean package -Djar.name=test3-%APP%'
                }
            }
        }
        stage('Depoly test3'){
            environment {
                ANYPOINT_CREDENTIALS = credentials('anypoint.credentials')
                ANYPOINT_CLIENT_ID = credentials('client_id')
                ANYPOINT_CLIENT_SECRET = credentials('client_secret')
            }
            when { changeset pattern: "test3/*" }
            steps{
                echo 'Depolying test3 app'
                dir("test3"){
                bat 'mvn deploy -DskipTests -DmuleDeploy -Danypoint.username=%ANYPOINT_CREDENTIALS_USR% -Danypoint.password=%ANYPOINT_CREDENTIALS_PSW% -Danypoint.platform.client_id=%ANYPOINT_CLIENT_ID% -Danypoint.platform.client_secret=%ANYPOINT_CLIENT_SECRET% -Danypoint.env=Sandbox -Danypoint.region=us-east-1 -Danypoint.workers=1 -Danypoint.name=test3-api -Djar.name=test3-%APP% -Dmule.artifact=%WORKSPACE%\\test3\\target\\test3-%APP%-mule-application.jar'
                }
            }
        }

    }


}
