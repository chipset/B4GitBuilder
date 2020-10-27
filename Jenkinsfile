pipeline {
    agent any
    environment {
        // Set up Environment Variables
        //CHANGE THIS SECTION FOR EACH SYSTEM 
        // OR set up a secret text credential for each of the variables.
        ENDEVOR=" --port 6002 --protocol http --reject-unauthorized false -i ENDEVOR --comment \"$actioncomment\" --ccid \"$actionccid\""

        ZOWE_OPT_HOSTNAME="10.175.80.65"
        ZOWE_OPT_HOST="$ZOWE_OPT_HOSTNAME"

        // z/OSMF Connection Details
        ZOWE_OPT_PORT="443"
        ZOWE_OPT_REJECT_UNAUTHORIZED=false

    }
    stages {
        stage('Generate Code') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'sr01', usernameVariable: 'ZOWE_OPT_USER', passwordVariable: 'ZOWE_OPT_PASSWORD')]) {
                    // Jenkins runs as a different user.  Uncomment lines below to install plugin. Other plugins could be added here.
                    //bat "npm config set @brightside:registry https://api.bintray.com/npm/ca/brightside"
                    //bat "C:/Users/Administrator/AppData/Roaming/npm/zowe.cmd plugins install @brightside/endevor@lts-incremental"
                    bat "C:/Users/Administrator/AppData/Roaming/npm/zowe.cmd endevor generate element $elementname --env $toenvironment --sn $tostageid --sys $tosystem --sub $tosubsystem --typ $totype $ENDEVOR"
                }
            }
        }

    }
}
