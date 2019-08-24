node{
    
    stage('clone'){
        checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'a14b9e5e-a271-40ee-be77-eb6595ff5342', url: 'https://github.com/csenapati12/java-tomcat-maven-example.git']]])
        echo "clone"
    }
    stage('maven build'){
        sh label: '', script: 'mvn package'
        echo "maven build"
    }
    stage('sonar analysis'){
        sh label: '', script: 'mvn package sonar:sonar'
        echo "sonar analysis"
    }
    stage('docker container'){
        echo "docker container"
    }
    stage('Docker Verification'){
        echo "Docker verification"
    }
    
}
