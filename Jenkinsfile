pipeline {
    agent {label 'SHPZR-1'}
    parameters {
        choice(name: 'branch', choices: ['master', 'develop'], description: 'selecting branches')
        string(name: 'build', defaultValue: 'package', description: 'Build')
    }
    triggers {
        pollSCM '* * * * *'
    }
    stages {
        stage('pull from vcs') {
         steps {
            git url: 'https://github.com/Qtalha/shopizer.git',
            branch: "${params.branch}"
           }
        }
        stage("build") {
            steps {
                sh "mvn ${params.build}"
            }
        }
    }
}