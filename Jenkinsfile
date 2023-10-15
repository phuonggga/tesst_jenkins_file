//properties([
//    parameters([
//    string(name: 'DEPLOY_ENV', defaultValue: 'TESTING', description: 'The target environment', )
//    booleanParam(defaultValue: false, name: 'ALL', description: 'Process all'),
//    booleanParam(defaultValue: false, name: 'OPTION_1', description: 'Process option 1'),
//    booleanParam(defaultValue: false, name: 'OPTION_2', description: 'Process options 2'),
//     ])
//    ])

pipeline {
    agent any
    stages {
        stage('Setup parameters') {
            steps {
                script { 
                    properties([
                        parameters([
                            choice(
                                choices: ['ONE', 'TWO'], 
                                name: 'PARAMETER_01'
                            ),
                            booleanParam(
                                defaultValue: true, 
                                description: '', 
                                name: 'BOOLEAN'
                            ),
                            text(
                                defaultValue: '''
                                this is a multi-line 
                                string parameter example
                                ''', 
                                 name: 'MULTI-LINE-STRING'
                            ),
                            string(
                                defaultValue: 'scriptcrunch', 
                                name: 'STRING-PARAMETER', 
                                trim: true
                            )
                        ])
                    ])
                }
            }
        }
    }   
}