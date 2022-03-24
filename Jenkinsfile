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
            when { changeset pattern: "test1/*", comparator: "REGEXP" }
            steps {
                echo 'Building test1'
                bat 'cd %WORKSPACE%\\test1'
                bat 'mvn clean package -Djar.name=test1-%APP%'
            }
        }
        stage('Depoly test1'){
            environment {
                ANYPOINT_CREDENTIALS = credentials('anypoint.credentials')
                ANYPOINT_CLIENT_ID = credentials('client_id')
                ANYPOINT_CLIENT_SECRET = credentials('client_secret')
            }
            when { changeset pattern: "test1/*", comparator: "REGEXP" }
            steps{
                echo 'Depolying test1 app'
                bat 'cd %WORKSPACE%\\test1'
                bat 'mvn deploy -DskipTests -DmuleDeploy -Danypoint.username=%ANYPOINT_CREDENTIALS_USR% -Danypoint.password=%ANYPOINT_CREDENTIALS_PSW% -Danypoint.platform.client_id=%ANYPOINT_CLIENT_ID% -Danypoint.platform.client_secret=%ANYPOINT_CLIENT_SECRET% -Danypoint.env=Sandbox -Danypoint.region=us-east-1 -Danypoint.workers=1 -Danypoint.name=test1 -Djar.name=test1-%APP% -Dmule.artifact=%WORKSPACE%\\test1\\target\\test1-%APP%-mule-application.jar'
            }
        }
        stage('App test2'){
            when { changeset pattern: "test2/*", comparator: "REGEXP" }
            steps {
                echo 'Building test2'
                bat 'cd %WORKSPACE%\\test1'
                bat 'mvn clean package -Djar.name=test2-%APP%'
            }
        }
        stage('Depoly test2'){
            environment {
                ANYPOINT_CREDENTIALS = credentials('anypoint.credentials')
                ANYPOINT_CLIENT_ID = credentials('client_id')
                ANYPOINT_CLIENT_SECRET = credentials('client_secret')
            }
            when { changeset pattern: ".test2/*", comparator: "REGEXP" }
            steps{
                echo 'Depolying test2 app'
                bat 'cd %WORKSPACE%\\test2'
                bat 'mvn deploy -DskipTests -DmuleDeploy -Danypoint.username=%ANYPOINT_CREDENTIALS_USR% -Danypoint.password=%ANYPOINT_CREDENTIALS_PSW% -Danypoint.platform.client_id=%ANYPOINT_CLIENT_ID% -Danypoint.platform.client_secret=%ANYPOINT_CLIENT_SECRET% -Danypoint.env=Sandbox -Danypoint.region=us-east-1 -Danypoint.workers=1 -Danypoint.name=test2 -Djar.name=test2-%APP% -Dmule.artifact=%WORKSPACE%\\test2\\target\\test1-%APP%-mule-application.jar'
            }
        }
        stage('App test3'){
            when { changeset pattern: "test3/*", comparator: "REGEXP" }
            steps {
                echo 'Building test3'
                bat 'cd %WORKSPACE%\\test3'
                bat 'mvn clean package -Djar.name=test3-%APP%'
            }
        }
        stage('Depoly test3'){
            environment {
                ANYPOINT_CREDENTIALS = credentials('anypoint.credentials')
                ANYPOINT_CLIENT_ID = credentials('client_id')
                ANYPOINT_CLIENT_SECRET = credentials('client_secret')
            }
            when { changeset pattern: "test3/*", comparator: "REGEXP" }
            steps{
                echo 'Depolying test3 app'
                bat 'cd %WORKSPACE%\\test3'
                bat 'mvn deploy -DskipTests -DmuleDeploy -Danypoint.username=%ANYPOINT_CREDENTIALS_USR% -Danypoint.password=%ANYPOINT_CREDENTIALS_PSW% -Danypoint.platform.client_id=%ANYPOINT_CLIENT_ID% -Danypoint.platform.client_secret=%ANYPOINT_CLIENT_SECRET% -Danypoint.env=Sandbox -Danypoint.region=us-east-1 -Danypoint.workers=1 -Danypoint.name=test3 -Djar.name=test3-%APP% -Dmule.artifact=%WORKSPACE%\\test3\\target\\test1-%APP%-mule-application.jar'
            }
        }

    }


}
