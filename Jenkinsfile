pipeline {
  agent {
    node {
      label 'principal'
    }
  }
  
  options {
    // Para ficheros de log
    //buildDiscarder(logRotator(daysToKeepStr: '3', numToKeepStr: '3')),
    
    buildDiscarder (logRotator(
      daysToKeepStr: '15',
        numToKeepStr: '10'
    ))
  }
  
  stages {
    stage("Cleanup Workspace"){
      steps {
        cleanWs()
        echo "Eliminado Workspace para Proyecto"
      }
    }
    
    stage("Code Checkout"){
      steps {
        checkout(
          $class: "GitSCM"
          branches: [[name: '*/main']],
          userRemoteConfigs: [[url:'https://github.com/spring-projects/spring-petclinic.git']]
        )
      }
    }
    
    stage("Unit Testing"){
      
      steps {
        echo "Running Unit Tests"
      }
    }
    
    stage("Code Analysis"){
      
      steps {
        echo "Running Code Analysis"
      }
    }
    
    stage("Build Deploy Code"){
      when{
        branch 'developer'
      }
      steps {
        echo "Building Artifact"
        echo "Deploying Artifact"
      }
    }
    
    
  }
}
