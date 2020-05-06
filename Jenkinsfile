// start of pipeline
pipeline {
  // where pipeline job will run
  agent {
    label 'ubuntu_slave'
  }
  
  // start of stages : build, test, deploy ...
  stages {
    // start of stage : build
    stage('build') {
      // start of running steps inside one stage
      steps {
        // invoke command to build with maven
        sh 'mvn clean install'
      }
    }
    
        // start of deploy state
    stage('deploy') {
      // define step to run
      steps {
        //invoke command to stop tomcat service
        sh 'sc stop Tomcat'
        sh 'ping http://13.127.145.206:9000/ -n 6'
        // copy war file from build target to webapp Tomcat folder
        sh 'xcopy /y C:\\jenkins_slave\\workspace\\GOL_Pipeline\\gameoflife-web\\target\\gameoflife.war "C:\\Program Files\\Apache Software Foundation\\Tomcat 7.0\\webapps"'
        //invoke command to start tomcat service      
        sh 'sc start Tomcat8'
      }
    } 

    
  } 
}

