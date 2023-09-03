pipeline {
    agent any

    stages {
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
                    steps {
                        echo 'Raspberry Pi builds'
                    }
                }
            }
        }
    }
}
