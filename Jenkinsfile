properties([
    parameters([
    string(name: 'DEPLOY_ENV', defaultValue: 'TESTING', description: 'The target environment', )
     ])
    ])

pipeline {
  agent any
  stages {
      stage ("Example") {
        steps {
         script{

       echo "Hello World"
       echo "${params.DEPLOY_ENV}"
       }
      }
    }
  }
}