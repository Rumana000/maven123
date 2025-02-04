pipeline
{
    agent any
    stages
    {
        stage('contdown')
        {
            steps
            {
                git 'https://github.com/Rumana000/maven123.git'
            }
            
        }
        stage('contbuild')
        {
            steps
            {
                sh 'mvn package'
            }
            
        }
        stage('contdeploy')
        {
            steps
            {
               deploy adapters: [tomcat9(credentialsId: 'f8947b36-6285-46b6-9e20-d6352d5a26bc', path: '', url: 'http://172.31.31.172:8080')], contextPath: 'testapp', war: '**/*.war' 
            }
            
        }
        stage('conttest')
        {
            steps
            {
                git 'https://github.com/Rumana000/FunctionalTesting.git'
                sh 'java -jar /var/lib/jenkins/workspace/declarativepipeline/testing.jar'
            }
            
        }
        stage('contdelivery')
        {
            steps
            {
               deploy adapters: [tomcat9(credentialsId: 'f8947b36-6285-46b6-9e20-d6352d5a26bc', path: '', url: 'http://172.31.24.87:8080')], contextPath: 'prodapp', war: '**/*.war'
            }
            
        }
    }
}
