pipeline {
    agent any
    environment {
        AQUA_URL = "https://github.com/bsvreddy1985/jenkinsfileWithCreds.git"
        AQUA_BRANCH = "main"
        
        }
    stgaes {
        stage('Fetch Code from GitHub'){
            steps{
                timeout (time: 10, unit: 'MINUTES'){
                    script{
                        try{
                            checkout ([ 
                                $class: 'GitSCM', branches: [[ name: env.AQUA_BRANCH ]],
                                doGenerateSubmoduleConfigurations: false,
                                extensions: [[$class: 'CleanBeforeCheckout'], [$class: 'RelativeTargetDirectory']], 
                                submoduleCfg: [],
                                userRemoteConfigs: [[ credentialsId: '5892fac1-bb03-465e-af0a-ee5623c9749b', url: env.AQUA_URL ]]
                            ])
                        }
                        catch (Exception err) {
                            println("Exception block: ${err}")
                            error "Failed to Clone AQUA_DEV URL from BitBucket. Please check the URL or Credential provided."
                        }
                    }
                }
            }
        }
    }
 }
