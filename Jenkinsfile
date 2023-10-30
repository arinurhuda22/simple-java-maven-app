node{
    checkout scm
    def image = docker.image('maven:3.9.0')
    image.inside{
       stage('Build'){
            sh 'mvn -B -DskipTests clean package'
        }
        stage('Test'){
            sh 'mvn test'
            junit 'target/surefire-reports/*.xml'
        }
        stage('Deliver'){
            sh './jenkins/scripts/deliver.sh'
        }
    }
}