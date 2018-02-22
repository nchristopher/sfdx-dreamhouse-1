pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh '''echo "Hub Org - $HUB_ORG"
echo "JWT Key - $JWT_KEY_FILE"
sfdx force:auth:jwt:grant --username "$HUB_ORG" --jwtkeyfile "$JWT_KEY_FILE" --clientid "$CONNECTED_APP_CONSUMER_KEY" --setdefaultdevhubusername --setalias DevHub'''
      }
    }
  }
}