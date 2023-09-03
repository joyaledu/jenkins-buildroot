pipeline {
    agent any

    stages {
        stage('Get Buildroot') {
            steps {
                echo 'Downloading Buildroot'
                    sh 'pwd'
                    sh 'wget https://buildroot.org/downloads/buildroot-2023.02.4.tar.gz'
                    sh 'tar -xvzf buildroot-2023.02.4.tar.gz'
                    sh 'mv buildroot-2023.02.4 buildroot'
                    sh 'ls'
            }
        }
        stage('Buildroot Builds') {
            parallel {
                stage('Beaglebone') {
                    stages {
                        stage('Prepare Config') {
                            steps {
                                sh 'rm -rf output-beaglebone'
                                sh 'mkdir output-beaglebone'
                                dir('output-beaglebone') {
                                    sh 'make -C ../buildroot O=$(pwd) beaglebone_defconfig'
                                }
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
