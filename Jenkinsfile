pipeline {
    agent any

    stages {
        stage('Get Buildroot') {
            steps {
                echo 'Downloading Buildroot'
                    sh 'pwd'
                    sh 'wget https://buildroot.org/downloads/buildroot-2023.02.4.tar.gz'
                    sh 'tar -xvzf buildroot-2023.02.4.tar.gz'
                    sh 'rm -rf buildroot'
                    sh 'mv buildroot-2023.02.4 buildroot'
                    sh 'ls'
            }
        }

        stage('Prepare beaglebone') {
            steps {
                sh 'rm -rf output-beaglebone'
                sh 'mkdir output-beaglebone'
                dir('output-beaglebone') {
                    sh 'make -C ../buildroot O=$(pwd) beaglebone_defconfig'
                }
            }
        }
        stage('Build beaglebone') {
            steps {
                dir('output-beaglebone') {
                    sh 'make'
                }
            }
        }

        stage('Prepare beaglebone_qt5') {
            steps {
                sh 'rm -rf output-beaglebone_qt5'
                sh 'mkdir output-beaglebone_qt5'
                dir('output-beaglebone_qt5') {
                    sh 'make -C ../buildroot O=$(pwd) beaglebone_qt5_defconfig'
                }
            }
        }
        stage('Build beaglebone_qt5') {
            steps {
                dir('output-beaglebone_qt5') {
                    sh 'make'
                }
            }
        }

        stage('Prepare raspberrypi2') {
            steps {
                sh 'rm -rf output-raspberrypi2'
                sh 'mkdir output-raspberrypi2'
                dir('output-raspberrypi2') {
                    sh 'make -C ../buildroot O=$(pwd) raspberrypi2_defconfig'
                }
            }
        }
        stage('Build raspberrypi2') {
            steps {
                dir('output-raspberrypi2') {
                    sh 'make'
                }
            }
        }

        stage('Prepare raspberrypi4') {
            steps {
                sh 'rm -rf output-raspberrypi4'
                sh 'mkdir output-raspberrypi4'
                dir('output-raspberrypi4') {
                    sh 'make -C ../buildroot O=$(pwd) raspberrypi4_defconfig'
                }
            }
        }
        stage('Build raspberrypi4') {
            steps {
                dir('output-raspberrypi4') {
                    sh 'make'
                }
            }
        }

        stage('Prepare raspberrypi4_64') {
            steps {
                sh 'rm -rf output-raspberrypi4_64'
                sh 'mkdir output-raspberrypi4_64'
                dir('output-raspberrypi4_64') {
                    sh 'make -C ../buildroot O=$(pwd) raspberrypi4_64_defconfig'
                }
            }
        }
        stage('Build raspberrypi4_64') {
            steps {
                dir('output-raspberrypi4_64') {
                    sh 'make'
                }
            }
        }

        stage('Prepare raspberrypizero2w') {
            steps {
                sh 'rm -rf output-raspberrypizero2w'
                sh 'mkdir output-raspberrypizero2w'
                dir('output-raspberrypizero2w') {
                    sh 'make -C ../buildroot O=$(pwd) raspberrypizero2w_defconfig'
                }
            }
        }
        stage('Build raspberrypizero2w') {
            steps {
                dir('output-raspberrypizero2w') {
                    sh 'make'
                }
            }
        }
    }
}
