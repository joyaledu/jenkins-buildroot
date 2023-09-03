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
        stage('make defconfig') {
            steps {
                script {
                    CONFIGS.tokenize(',').each {
                        echo "make ${it}_defconfig"
                    }
                }
            }
        }
    }
}
