properties([
    parameters([
    string(name: 'DEPLOY_ENV', defaultValue: 'TESTING', description: 'The target environment', )
    booleanParam(defaultValue: false, name: 'ALL', description: 'Process all'),
    booleanParam(defaultValue: false, name: 'OPTION_1', description: 'Process option 1'),
    booleanParam(defaultValue: false, name: 'OPTION_2', description: 'Process options 2'),
     ])
    ])

pipeline {
  agent any
  stages {
      stage ("Example") {
        steps {
         script{

       echo "Hello World"
       echo "${params.name}"
       }
      }
    }
  }
}