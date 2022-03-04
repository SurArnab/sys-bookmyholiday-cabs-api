pipeline {

  agent any
  environment {
    //adding a comment for the commit test
    DEPLOY_CREDS = credentials('admin')
    MULE_VERSION = '4.4.0'
    BG = "Apisero"
    WORKER = "Micro"
    DEPLOY_CREDS_USR = "arnabtsur2"
	DEPLOY_CREDS_PSW = "Arnab@2410"
  }
  stages {
    stage('Build') {
      steps {
            bat 'mvn -B -U -e -V clean -gs -DskipTests package'
      }
    }

    /* stage('Test') {
      steps {
          bat "mvn test"
      }
    } */

    stage('Deploy Development') {
      environment {
        ENVIRONMENT = 'dev'
        APP_NAME = 'sys-bookmyholiday-cabs-api-v2'
		CLIENT_ID = '4658f94537f04235a809ca690cb8b087'
		CLIENT_SECRET = '335918A2462d4a39b70d354637587930'
		ENV = 'dev'
      }
      steps {
            bat 'mvn -U -V -e -B -gs -DskipTests deploy -DskipMunitTests -DmuleDeploy -Dmule.version="%MULE_VERSION%" -Danypoint.username="%DEPLOY_CREDS_USR%" -Danypoint.password="%DEPLOY_CREDS_PSW%" -Dcloudhub.app="%APP_NAME%" -Dcloudhub.environment="%ENVIRONMENT%" -Dcloudhub.bg="%BG%" -Dcloudhub.worker="%WORKER%" -Danypoint.platform.client_id="%CLIENT_ID%" -Danypoint.platform.client_secret=%CLIENT_SECRET% -Denv = "%ENV%"' 
      }
    }
    /* stage('Deploy Production') {
      environment {
        ENVIRONMENT = 'Production'
        APP_NAME = '<PROD-API-NAME>'
      }
      steps {
            bat 'mvn -U -V -e -B -gs %M2SETTINGS% -DskipTests deploy -DmuleDeploy -Dmule.version="%MULE_VERSION%" -Danypoint.username="%DEPLOY_CREDS_USR%" -Danypoint.password="%DEPLOY_CREDS_PSW%" -Dcloudhub.app="%APP_NAME%" -Dcloudhub.environment="%ENVIRONMENT%" -Dcloudhub.bg="%BG%" -Dcloudhub.worker="%WORKER%"'
      }
    } */
  }
}