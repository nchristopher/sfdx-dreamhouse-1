pipeline {
  agent any
  stages {
    stage('Build') {
      parallel {
        stage('Build') {
          steps {
            sh 'sfdx force:auth:jwt:grant --username "$HUB_ORG" --jwtkeyfile "$JWT_KEY_FILE" --clientid "$CONNECTED_APP_CONSUMER_KEY" --setdefaultdevhubusername --setalias DevHub'
          }
        }
        stage('Create Scratch Org') {
          steps {
            sh '''SCRATCH_ORG_ALIAS="Scratch-ORG:Push-Build-${BUILD_NUMBER}"
sfdx force:org:create --definitionfile "config/project-scratch-def.json" --setalias "${SCRATCH_ORG_ALIAS}" --setdefaultusername'''
          }
        }
        stage('Push Source') {
          steps {
            sh 'sfdx force:source:push'
          }
        }
      }
    }
  }
}