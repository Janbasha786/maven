pipeline
{
    agent any
    stages
    {
        stage('continuousdownload')
        {
            steps
            {
                git 'https://github.com/intelliqittrainings/maven.git'
            }
        }
        stage('continuousbuild')
        {
            steps
            {
                sh 'mvn package'
            }
        }
        stage('continuousdeployment')
        {
            steps
            {
                deploy adapters: [tomcat9(credentialsId: '21be0d36-1560-4bcb-a643-a6d11fdaaa35', path: '', url: 'http://172.31.30.137:8080')], contextPath: 'testapk', war: '**/*.war'
            }
        }
        stage('continuoustesting')
        {
            steps
            {
                git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
                sh 'java -jar /var/lib/jenkins/workspace/declarativepipeline1/testing.jar'
            }
        }
        stage('continuousdelivery')
        {
            steps
            {
                deploy adapters: [tomcat9(credentialsId: '21be0d36-1560-4bcb-a643-a6d11fdaaa35', path: '', url: 'http://172.31.18.66:8080')], contextPath: 'prodapk', war: '**/*.war'
            }
        }
        
    }
}
