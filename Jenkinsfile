def jobParameters = [:]
jobParameters['INSTANCE_NAME'] = params.INSTANCE_NAME
jobParameters['WORKSPACE'] = params.WORKSPACE
def paramsObjects = []
jobParameters.each {
  key, value ->
    paramsObjects.push([$class: 'StringParameterValue', name: key, value: value])
}    
[
    [$class:StringParameterValue, name:param1, value:value1],
    [$class:StringParameterValue, name:param2, value:value2]
]
pipeline{
    stages {
        stage('Test1')
        steps {
            script {
                echo 'Starting "test1"'
                build job: './test1'
                parameters:
                paramsObjects
            }
        }
        stage('Test2')
        steps {
            script {
                echo 'Starting "test2"'
                build job: './test2',
                        parameters: paramsObjects
            }
        }
    }
}
