node('built-in') {
    stage('ContinuousDownload') {
        echo 'Downloading source code from GitHub repository'
        git 'https://github.com/divyarajprankur/maven.git'
    }
    
    stage('ContinuousBuild') {
        sh label: 'Build Application with Maven', script: 'mvn package'
    }
    
    stage('ContinuousDeployment') {
        sh label: 'Deploy to QA Environment', 
           script: 'scp /home/ubuntu/.jenkins/workspace/jenkinspipeline/webapp/target/webapp.war ubuntu@172.31.10.206:/var/lib/tomcat10/webapps/qaaenv.war'
    }
    
    stage('ContinuousTest') {
        sh label: 'Execute Test Verification', script: 'echo "TESTING IS SUCCESSFULL !!!"'
    }
    
    stage('ContinuousDelivery') {
        sh label: 'Deploy to Production Environment', 
           script: 'scp /home/ubuntu/.jenkins/workspace/jenkinspipeline/webapp/target/webapp.war ubuntu@172.31.0.132:/var/lib/tomcat10/webapps/productionenv.war'
    }
}
