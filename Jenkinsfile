pipeline {
    agent any

    stages {
        stage('Get Buildroot') {
            steps {
                echo 'Downloading Buildroot'
                sh 'pwd'
                sh 'wget https://buildroot.org/downloads/buildroot-2023.02.4.tar.gz'
            }
        }
        stage('Buildroot Builds') {
            parallel {
                stage('Beaglebone') {
                    stages {
                        stage('Prepare Config') {
                            steps {
                                echo 'Preparing Config'
                            }
                        }
                        stage('Build Image') {
                            steps {
                                echo 'Building Image'
                            }
                        }
                    }
                }
                stage('Raspberry Pi') {
                    stages {
                        stage('Prepare Config') {
                            steps {
                                echo 'Preparing Config'
                            }
                        }
                        stage('Build Image') {
                            steps {
                                echo 'Building Image'
                            }
                        }
                    }

                }
            }
        }
    }
}
