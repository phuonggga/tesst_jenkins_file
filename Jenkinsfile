 def dem = ''
 pipeline {
    agent any
        stages {
            stage('Parameters'){
                steps {
                    script {
                    properties([
                            parameters([
                            text(
                                defaultValue: '''''', 
                                name: 'application_servers',
                                description: 'Please provide semicolon delimited (;) application server list ', 
                            ),
                            text(
                                defaultValue: '''''', 
                                name: 'demo',
                                description: 'Please provide semicolon delimited (;) application server list ', 
                            ),
                                [$class: 'CascadeChoiceParameter', 
                                    choiceType: 'PT_CHECKBOX', 
                                    description: 'Select Services',
                                    name: 'application_services_list', 
                                    referencedParameters: 'application_servers', 
                                    script: 
                                        [$class: 'GroovyScript', 
                                        fallbackScript: [
                                                classpath: [], 
                                                sandbox: false, 
                                                script: "return['']"
                                                ], 
                                        script: [
                                                classpath: [], 
                                                sandbox: false, 
                                                script: '''
                                                if (application_servers.length() > 0){
                                                    return["heartbeat_consumer", "surgeon_cloud_login", "system_configuration"]
                                                }
                                                '''
                                            ] 
                                    ]
                                ],
                                [$class: 'DynamicReferenceParameter', 
                                    choiceType: 'ET_FORMATTED_HTML', 
                                    description: 'enter job params',
                                    name: 'hb_job_params', 
                                    referencedParameters: 'application_services_list', 
                                    script: 
                                        [$class: 'GroovyScript', 
                                        fallbackScript: [
                                                classpath: [], 
                                                sandbox: false, 
                                                script: "return['']"
                                                ], 
                                        script: [
                                                classpath: [], 
                                                sandbox: false, 
                                                script: '''
                                                if (application_services_list.contains('heartbeat_consumer')){
                                                    return """<textarea name=\"CHECK\" rows=\"5\" class=\"setting-input   \">${dem}</textarea>"""

                                                }
                                                '''
                                            ] 
                                    ],
                                omitValueField: true
                                ],
                            ])
                        ])
                    }
                }
            }
            stage("check"){
                steps{
                    echo "${params.hb_job_params}"
                    echo "${dem}"
                }
                
            }
        }
    }