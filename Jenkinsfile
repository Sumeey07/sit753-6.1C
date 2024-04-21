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
            always {
              emailext (
                subject: "Pipeline status: ${currentBuild.result}",
                body: '''<html>
                            <body>
                                <p>Build Status: ${currentBuild.result}</p>
                                <p>Build Number: ${currentBuild.number}</p>
                                <p>Check the <a href="${env.BUILD_URL}">console output</a>.</p>
                            </body>
                        </html>''',
                to: 'narwani.sumeet92@gmail.com',
                from: 'jenkins@example.com',
                replyTo: 'jenkins@example.com',
                mimeType: 'text/html'
              )
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
}