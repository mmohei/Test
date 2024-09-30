pipeline {
    agent any
    
    parameters {
        string(defaultValue: 'main', description: 'Enter Branch Name', name: 'branchname')
    }

    environment {
        REMOTE_SERVER = '192.168.0.12'
        REMOTE_USER = 'jenkins'
        WEBSITE_NAME = 'test'
    }

    stages {
        stage('Checkout') {
            steps {
                checkout([
                    $class: 'GitSCM',
                    branches: [[name: params.branchname]],  // Added params to access the parameter
                    userRemoteConfigs: [[
                        url: 'https://github.com/mmohei/Test.git',
                        credentialsId: 'c322d850-7677-484f-9f01-f0e8e35ba055'
                    ]]
                ])
            }
        }

        stage('Build') {
            steps {
                // Assuming this is a Windows-based environment with .NET installed
                bat "dotnet publish -c Release"
            }
        }
    }
}
