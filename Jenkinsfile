node(){
    properties([parameters([choice(choices: ["Deploy_L1_L2_L3" , "L4" , "L6"].join("\n"),description: 'Select the Environment to deploy', name: 'ENV_NAME')])])

   echo  "Environment is  ${params.ENV_NAME}"
    stage('clone'){
        checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'a14b9e5e-a271-40ee-be77-eb6595ff5342', url: 'https://github.com/csenapati12/java-tomcat-maven-example.git']]])
        echo "clone"
    }
    stage('maven build'){
        sh label: '', script: 'mvn package'
        echo "maven build"
    }
    stage('sonar analysis'){
      //sh label: '', script: 'mvn package sonar:sonar'
        echo "sonar analysis"
    }
    stage('docker container'){
        echo "docker container"
        sh """
        docker build -t myimage1 .
        docker run -d -p 8831:8080 myimage1
        """
    }
    stage('Docker Verification'){
        echo "Docker verification"
    }
    
}
