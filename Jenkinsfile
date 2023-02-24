pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                checkout scmGit(branches: [[name: '*/abdullah-branch']], extensions: [], userRemoteConfigs: [[credentialsId: '28611953-a613-42c5-8a50-7872fef90589', url: 'https://github.com/NUCES-ISB/i192043_i190527_A1-chatgpt-wrapper']])
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
                bat '''pylint ../ChatGPT-Wrapper-SAN --exit-zero '''
            }
        }
        stage('Run black') {
            steps {
                bat '''python -m black ../ChatGPT-Wrapper-SAN'''
            }
        }
    }
}
