
pipeline {
    agent any
    parameters {
        choice(
            name: 'CHOICE_LIST_1',
            choices: ['a', 'b', 'c'],
            description: 'Make a choice'
        )
        activeChoiceParam(
            name: 'PARAM_2',
            description: 'Enter param 2',
            choiceType: 'PT_SINGLE_SELECT',
            script: [
                $class: 'GroovyScript',
                fallbackScript: [
                    classpath: [],
                    sandbox: false,
                    script: "return ['']"
                ],
                script: [
                    classpath: [],
                    sandbox: false,
                    script: '''
                        if (params.CHOICE_LIST_1 == 'b') {
                            return ['']
                        } else {
                            return ['param 2']
                        }
                    '''
                ]
            ]
        )
        activeChoiceParam(
            name: 'PARAM_3',
            description: 'Enter param 3',
            choiceType: 'PT_SINGLE_SELECT',
            script: [
                $class: 'GroovyScript',
                fallbackScript: [
                    classpath: [],
                    sandbox: false,
                    script: "return ['']"
                ],
                script: [
                    classpath: [],
                    sandbox: false,
                    script: '''
                        if (params.PARAM_2 == 'param 2') {
                            return ['param 3']
                        } else {
                            return ['']
                        }
                    '''
                ]
            ]
        )
    }
    stages {
        stage('Example') {
            steps {
                echo "You chose ${params.CHOICE_LIST_1}, ${params.PARAM_2}, ${params.PARAM_3}"
            }
        }
    }
}