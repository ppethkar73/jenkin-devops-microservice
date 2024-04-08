// DECLARATIVE
pipeline {
	// agent any
	agent { docker { image 'maven:3.6.3'} 
	}
	// environment {
	// 	dockerHome = tool 'myDocker'
	// 	mavenHome = tool 'myMaven'
	// 	PATH = "$dockerHome/bin;$mavenHome/bin;$PATH"
	// }
	stages {
		stage('Checkout') {
			steps {
				sh 'mvn --version'
				//echo "MYJAVA_HOME - $env.JAVA_HOME"
				//sh 'ls -al /opt/java/openjdk'
				echo "Build"
				echo "Build Number - $env.BUILD_NUMBER"
				echo "Build ID - $env.BUILD_ID"
				echo "Job Name - $env.JOB_NAME"
				echo "Build Tag - $env.BUILD_TAG"
				echo "Build URL - $env.BUILD_URL"

			}
		}
		stage('Compile') {
			steps {
				sh 'mvn clean compile'
			}
		}
		stage('Test') {
			steps {
				sh 'mvn test'
			}
		}
		stage('Integration Test') {
			steps {
				sh ' mvn failsafe:integration-test failsafe:verify'
			}
		}
	} 
	post {
		always {
			echo 'Im awesome, I run always'
		}
		success {
			echo 'I run when you are successful'
		}
		failure {
			echo 'I run when you fail'
		}
	}
}
