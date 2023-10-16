pipeline {
    agent any
    parameters {
        choice(
            name: 'CHOICE_LIST_1',
            choices: ['a', 'b', 'c'],
            description: 'Make a choice'
        )
        cascadeChoiceParam(
            name: 'PARAM_2',
            description: 'Enter param 2',
            choiceType: 'PT_SINGLE_SELECT',
            referencedParameters: 'CHOICE_LIST_1',
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
                        if (CHOICE_LIST_1 == 'b') {
                            return ['']
                        } else {
                            return ['param 2']
                        }
                    '''
                ]
            ]
        )
        cascadeChoiceParam(
            name: 'PARAM_3',
            description: 'Enter param 3',
            choiceType: 'PT_SINGLE_SELECT',
            referencedParameters: 'PARAM_2',
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
                        if (PARAM_2 == 'param 2') {
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