pipeline {
    agent any

    stages {
        stage('copyArtifacts'){
            steps{
                copyArtifacts filter: '**/*.war', fingerprintArtifacts: true, projectName: 'maven_build', selector: lastSuccessful()
            }
        }
        stage("Deploy"){
            steps{
                deploy adapters: [tomcat9(credentialsId: '432c4b48-28b7-423f-8e5c-02f85853390f',
                        path: '', url: 'http://172.31.38.171:8888/')],
                                  contextPath: null, war: '**/*.war'       
            }
        }
    }
}

