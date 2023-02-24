pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                checkout scmGit(branches: [[name: '*/hunaid-branch']], extensions: [], userRemoteConfigs: [[credentialsId: '8e8069e3-2048-4048-8976-46874166268c', url: 'https://github.com/NUCES-ISB/i192043_i190527_A1-chatgpt-wrapper']])
            }
        }
        stage('Install dependencies') {
            steps {
                bat '''pip install pylint black setuptools
                        pip install --upgrade setuptools
                        pip install -r requirements.txt'''
            }
        }
        stage('Run pylint') {
            steps {
                bat '''pylint ../MLOps-A1-Test2 --exit-zero '''
            }
        }
        stage('Run black') {
            steps {
                bat '''python -m black ../MLOps-A1-Test2'''
            }
        }
    }
}
