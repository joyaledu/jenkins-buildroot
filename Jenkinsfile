pipeline {
    agent any

    stages {
        stage('Get Buildroot') {
            steps {
                echo 'Downloading Buildroot'
                sh '''
                    pwd
                    wget https://buildroot.org/downloads/buildroot-2023.02.4.tar.gz
                    mv buildroot-2023.02.4.tar.gz buildroot.tar.gz
                    tar -xvzf buildroot.tar.gz
                    ls
                '''
            }
        }
        stage('Buildroot Builds') {
            parallel {
                stage('Beaglebone') {
                    stages {
                        stage('Prepare Config') {
                            steps {
                                sh '''
                                    mkdir output-beaglebone'
                                    make -C ../buildroot O=$(pwd) menuconfig
                                '''
                            }
                        }
                        stage('Build Image') {
                            steps {
                                dir('output-beaglebone') {
                                    sh 'make clean'
                                }
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
