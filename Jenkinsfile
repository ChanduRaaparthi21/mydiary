pipeline 
{
    agent any

    stages {

        stage('clone repository') {

            steps {

                checkout scm
            }
        }

stage('Build') {

            steps {
sh 'mvn clean package'
            }
        
}
stage('unit test'){
steps{
           sh 'mvn test'
}


        post{
                      always{

    junit '**/target/surefire-reports/TEST-*.xml'     

}
}
                       }

stage('Deploy') {

            steps {

                   sh 'aws s3 sync ./build s3://my.bucket --only-show-errors'
            }
        }

    stage ('end to end testing'){
                      steps{
                          sh(script: 'NO_COLOR=1 node_modules/.bin/cypress run || true')
}                          
                  }

stage('prod deployment'){
              steps{
                              sh './deploy production'
}  
}

stage ('email'){
    steps{
post {
always {
        emailext (
            subject: 'mailindication',
            body: 'The Build is complete and success'
            to: 'vamsienjoy1@gmail.com'
            attachmentspattern: '**/*.log'
            )
} 
}
}
}
}
}
