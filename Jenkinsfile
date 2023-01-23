pipeline {

    agent any
    stages {

        stage('Checkout Codebase'){
            steps{
                cleanWs()
                checkout scm: [$class: 'GitSCM', branches: [[name: '*/main']],userRemoteConfigs:
                [[url: 'https://github.com/bhagwatamols/junitrepo.git']]]
            }
        }

        stage('Build'){
            steps{
                bat 'mkdir lib'
				dir("C:\\ProgramData\\Jenkins\\.jenkins\\workspace\\JUNIT_TEST\\lib\\") {
				
				}
		
		        bat 'copy D:\\zlib\\*'
		dir("cd C:\\ProgramData\\Jenkins\\.jenkins\\workspace\\JUNIT_TEST\\src\\") {
				bat 'cd'
				}        

       
                bat 'javac -cp ../lib/* CarTest.java Car.java App.java'
            }
        }

        stage('Test'){
            steps{
                bat 'chdir src/'
                bat 'java -jar ../lib/junit-platform-console-standalone-1.7.0-all.jar -cp "." --select-class CarTest --reports-dir="reports"'
                junit 'src/reports/*-jupiter.xml'
            }
        }

        stage('Deploy'){
            steps{
                bat 'chdir src/'
                bat 'java App' 
            }
        }
    }

}
