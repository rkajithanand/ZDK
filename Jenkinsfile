#!groovy

pipeline {
    agent any  // No agent allocated at the start

    stages {
        stage('Push') {
            // Allocate an agent for this stage
            // This block ensures the commands are run on an available agent.
            
            tools {
                customTool 'toolbelt'
            }
            environment {
                MYTOOL_HOME = tool name: 'toolbelt', type: 'org.jenkinsci.plugins.customtools.CustomTool'
            }

            steps {
                echo 'Started the push...'
                sh '$MYTOOL_HOME/zdk org:push'
            }
        }

        // stage('Test') {
        //     node {
        //         echo 'Running tests...'
        //         sh 'echo "Tests executed."'
        //     }
        // }

        // stage('Deploy') {
        //     node {
        //         echo 'Deploying...'
        //         sh 'echo "Application deployed."'
        //     }
        // }
    }
}
