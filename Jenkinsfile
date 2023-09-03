
def jobs = ["beaglebone", "raspberrypi2", "raspberrypi4_64"]
 
def parallelStagesMap = jobs.collectEntries {
    ["${it}" : generateStage(it)]
}
 
def generateStage(job) {
    return {
        stage("stage: ${job}") {
            steps {
                echo "configuring ${job}"
                sh "rm -rf output-${job}"
                sh "mkdir output-${job}"
                dir("output-${job}") {
                    sh "make -C ../buildroot O=$(pwd) $\{job}" + "_defconfig"
                }
            }
        }
    }
}
 
pipeline {
    agent any
 
    stages {
        stage('fetch buildroot') {
            steps {
                echo 'Downloading Buildroot'
                sh 'pwd'
                // sh 'wget https://buildroot.org/downloads/buildroot-2023.02.4.tar.gz'
                sh 'cp /tmp/buildroot-2023.02.4.tar.gz .'
                sh 'tar -xvzf buildroot-2023.02.4.tar.gz'
                sh 'rm -rf buildroot'
                sh 'mv buildroot-2023.02.4 buildroot'
                sh 'ls'
            }
        }
 
        stage('config') {
            steps {
                script {
                    parallel parallelStagesMap
                }
            }
        }

        stage('building') {
            steps {
                script {
                    for(int i=0; i < jobs.size(); i++) {
                        stage(jobs[i]){
                            steps {
                                dir('output-' + jobs[i]) {
                                    sh 'make clean'
                                }
                            }
                        }
                    }
                }
            }
        }
    }
}
