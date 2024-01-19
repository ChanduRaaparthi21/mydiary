pipeline 
{
    agent any

    stages {

        stage('Hello') {

            steps {

                echo 'Hello World'
            }
        }

stage('Build') {

            steps {

                echo 'Test'
            }
        }

stage('Deploy') {

            steps {

                echo 'Deploy'
            }
        }

    }
post {

always {
        emailext body: 'pipeline', subject: 'mailindication', to: 'cvamsikrishna949494@gmail.com'
} 

}
}
