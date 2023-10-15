properties([
    parameters([
        choice(
            name: 'ENV',
            choices: [
                'dev',
                'prod'
            ]
        ),
        [$class: 'ChoiceParameter',
            choiceType: 'PT_RADIO',
            filterLength: 1,
            filterable: false,
            name: 'CHOICES',
            script: [
                $class: 'GroovyScript',
                //fallbackScript: [
                //    classpath: [],
                //    sandbox: false,
                //    script: 'return ["Check Jenkins ScriptApproval page"]'
                //],
                script: [
                    classpath: [],
                    sandbox: false,
                    script: 
                        'if (ENV == "dev") { return ["One","Two:selected"] } else { return ["2","T23:selected"]}'
                ]
            ]
        ]
    ])
])

pipeline {
    agent any

    stages {
        stage('Print the Values') {
            steps {
                echo "Environment: ${params.ENV}"
                echo "Choice: ${params.CHOICES}"
            }
        }
    }
}