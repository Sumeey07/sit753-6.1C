pipeline {
  agent any

  stages {
      stage('Build') {
        steps {
            echo 'Task: Build the code using a build automation tool'
            echo 'Tool: Maven'
        }
      }
      stage('Unit and Integration Tests') {
        steps {
            echo 'Task: Run unit tests and integration tests'
            echo 'Tools: JUnit for unit tests, Selenium for integration tests'
        }
      }
      stage('Code Analysis') {
        steps {
            echo 'Task: Integrate a code analysis tool'
            echo 'Tool: SonarQube'
        }
      }
      stage('Security Scan') {
        steps {
            echo 'Task: Perform a security scan'
            echo 'Tool: OWASP ZAP'
        }
        post {
          success {
              echo 'Security Scan Successful. Sending notification email.'
              script {
                def logFile = 'security_scan_log.txt'
                currentBuild.rawBuild.getLog(1000).writeTo(logFile)
                emailext to: 'narwani.sumeet92@gmail.com', subject: 'Security Scan Successful', body: 'The security scan was successful. Console output attached.', attachmentsPattern: logFile
              }
          }
          failure {
            echo 'Security Scan Failed. Sending notification email.'
            script {
              def logFile = 'security_scan_log.txt'
              currentBuild.rawBuild.getLog(1000).writeTo(logFile)
              emailext to: 'narwani.sumeet92@gmail.com', subject: 'Security Scan Failed', body: 'The security scan failed. Console output attached.', attachmentsPattern: logFile
            }
          }
        }
      }
      stage('Deploy to Staging') {
        steps {
            echo 'Task: Deploy the application to a staging server'
            echo 'Tool: AWS CodeDeploy'
        }
      }
      stage('Integration Tests on Staging') {
        steps {
            echo 'Task: Run integration tests on the staging environment'
            echo 'Tool: Selenium'
        }
      }
      stage('Deploy to Production') {
        steps {
            echo 'Task: Deploy the application to a production server'
            echo 'Tool: AWS CodeDeploy'
        }
      }
  }

  post {
    success {
        echo 'Notification: Build Successful. Email sent.'
        script {
          def logFile = 'build_log.txt'
          currentBuild.rawBuild.getLog(1000).writeTo(logFile)
          emailext to: 'narwani.sumeet92@gmail.com', subject: 'Build Successful', body: 'The build was successful. Console output attached.', attachmentsPattern: logFile
        }
    }
    failure {
        echo 'Notification: Build Failed. Email sent.' 
        script {
          def logFile = 'build_log.txt'
          currentBuild.rawBuild.getLog(1000).writeTo(logFile)
          emailext to: 'narwani.sumeet92@gmail.com', subject: 'Build Failed', body: 'The build failed. Console output attached.', attachmentsPattern: logFile
        }
    }
  }
}