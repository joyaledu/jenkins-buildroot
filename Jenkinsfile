
def jobs = ["beaglebone", "raspberrypi2", "raspberrypi4_64"]
 
def parallelStagesMap = jobs.collectEntries {
    ["${it}" : generateStage(it)]
}
 
def generateStage(job) {
    return {
        stage("stage: ${job}") {
                echo "This is ${job}."
        }
    }
}
 
pipeline {
    agent none
 
    stages {
        stage('non-parallel stage') {
            steps {
                echo 'This stage will be executed first.'
            }
        }
 
        stage('parallel stage') {
            steps {
                script {
                    parallel parallelStagesMap
                }
            }
        }

        for (int i = 0; i < jobs.length; i++) {
            generateStage(jobs[i]);
        }
    }
}