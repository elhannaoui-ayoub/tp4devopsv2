pipeline {
environment {
registry = "aelhannaoui/job3tp4"
registryCredential = 'dockerhubv'
dockerImage = ''
}
agent any
stages {
stage('Cloning Git') {
steps {
git 'https://github.com/elhannaoui-ayoub/tp4devopsv2'
}
}
stage('Building image') {
steps{
script {
dockerImage = docker.build registry + ":$BUILD_NUMBER"
}
}


}




stage('Publish Image') {
steps{
script {
docker.withRegistry( '', registryCredential ) {
dockerImage.push()
}
}
}
}

stage('Deploy image') {
steps{
bat "docker run -d -p 8086:80 $registry:$BUILD_NUMBER"
}
}


}
}