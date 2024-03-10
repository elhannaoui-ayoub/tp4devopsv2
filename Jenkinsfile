pipeline {
environment {
registry = "aelhannaoui/job2tp4v2"
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
stage('Test image') {
steps{
script {

echo "Tests passed"
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
bat "docker run -d $registry:$BUILD_NUMBER"
}
}


}
}