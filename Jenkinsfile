properties([
    parameters([
        [$class: 'ChoiceParameter', 
            choiceType: 'PT_SINGLE_SELECT', 
            description: 'Select the Environemnt from the Dropdown List', 
            filterLength: 1, 
            filterable: false, 
            name: 'Env', 
            script: [
                $class: 'GroovyScript', 
                fallbackScript: [
                    classpath: [], 
                    sandbox: false, 
                    script: 
                        "return['Could not get The environemnts']"
                ], 
                script: [
                    classpath: [], 
                    sandbox: false, 
                    script: 
                        "return['dev','stage','prod']"
                ]
            ]
        ],
        [$class: 'CascadeChoiceParameter', 
            choiceType: 'PT_SINGLE_SELECT', 
            description: 'Select the AMI from the Dropdown List',
            name: 'AMI_List', 
            referencedParameters: 'Env', 
            script: 
                [$class: 'GroovyScript', 
                fallbackScript: [
                        classpath: [], 
                        sandbox: false, 
                        script: "return['Could not get Environment from Env Param']"
                        ], 
                script: [
                        classpath: [], 
                        sandbox: false, 
                        script: '''
                        if (Env.equals("dev")){
                            return["ami-sd2345sd", "ami-asdf245sdf", "ami-asdf3245sd"]
                        }
                        else if(Env.equals("stage")){
                            return["ami-sd34sdf", "ami-sdf345sdc", "ami-sdf34sdf"]
                        }
                        else if(Env.equals("prod")){
                            return["ami-sdf34sdf", "ami-sdf34ds", "ami-sdf3sf3"]
                        }
                        '''
                    ] 
            ]
        ],
        [$class: 'DynamicReferenceParameter', 
            choiceType: 'ET_FORMATTED_HTML', 
            description: 'Select the  AMI based on the following infomration', 
            name: 'Image_Information', 
            referencedParameters: 'AMI_List', 
            script: 
                [$class: 'GroovyScript', 
                script: 'return["Could not get AMi Information"]', 
                script: [
                    script: '''
                            if(AMI_List.contains("ami-sd2345sd")){
                                return """<textarea name=\"value\" rows=\"5\" class=\"setting-input   \"></textarea>"""
                            }
                            '''
                        ]
                ]
        ]
    ])
])

pipeline {
    agent any
        stages {
            stage('Parameters'){
                when{
                    expression {
                        params.Env == 'dev'
                    }
                }
                steps {
                    script {
                        echo "Environment: ${params.Env}"
                        echo "AMIL: ${parms.AMI_List}"
                        echo "demo: ${parms.Image_Information}"
                }
            }
            stage('demo'){
                when{
                    expression {
                        params.Env == 'prod'
                    }
                }
                steps {
                    script {
                        echo "dadasdasd"
                    }
                }
            }
        }
    }   
}