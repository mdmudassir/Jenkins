
pipeline {
  agent any
	parameters {
	choice(name: 'Gitbranch', choices:['main', 'feature'], description: 'Select branch')  
	}
    stages {
        stage('Prepare and Checkout') {
            steps {
                script {
                    env.StartTime = bat(returnStdout: true,
                    script: ''' 
                    @echo off
                    echo "%TIME%"
                    ''').trim()
                }
                checkout changelog: false, poll: false,
                scm: [$class: 'GitSCM',
                branches: [[name: "*/$GitBranch"]],
                extensions: [],
                userRemoteConfigs: [[credentialsId: 'Github', url: 'https://github.com/mdmudassir/Jenkins.git']]]
            }
        }
	stage("build") {
		steps {
			echo "${StartTime} building the application"
		}
	}
	stage("test") {
		steps {
			echo 'testing the application'
		}
	}
	stage("deploy") {
		steps {
			echo 'deploying the application'
		}
	}
}
}


