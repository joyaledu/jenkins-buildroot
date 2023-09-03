pipeline {
    agent any

    environment {
        CONFIGS = 'beaglebone,raspberrypi2,raspberrypi4_64'
    }

    stages {
        stage('Get Buildroot') {
            steps {
                echo 'Downloading Buildroot'
            }
        }
        stage('Buildroot Builds') {
            parallel {
                script {
                    CONFIGS.tokenize(',').each {
                        stage('${it}') {
                            stages {
                                stage('make ${it}_defconfig') {
                                    steps {
                                        echo 'make ${it}_defconfig'
                                    }
                                }
                                stage('Build ${it} image') {
                                    steps {
                                        echo 'make'
                                    }
                                }
                            }
                        }
                    }
                }
            }
        }
    }
}
