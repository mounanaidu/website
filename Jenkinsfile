def gv
pipeline{
    agent any
    // environment{
    //     NEW_VERSION = "1.0.1"
    //     SERVER_CREDENTIAL = credential('credential-id-from Jenkins UI')
    // }
    stages {
        stage("This stage will be running parallely, if each step takes 5sec then this totally taking 5sec"){
            parallel{
                stage('build reporting function'){
                    steps{
                        echo "This is building reporting module"
                    }
                }
                stage('build check-in functions'){
                    steps{
                        echo "This is building reporting module"
                    }
                }
            }
        }
        stage("init"){
            steps {
                script{
                    gv = load("script.groovy")
                }
            }
        }
        stage("build"){
            steps {
                script{
                    gv.buildApp()
                }
                echo "This is the build step"
            }
        }

        stage("test") {
            // when{
            //     expression{
            //         BRANCH_NAME == 'dev' && CODE_CHANGES==true
            //     }
            // }
            steps {
                echo "This is the test step in version ${NEW_VERSION}"
            }
        }

        stage("deploy") {
            steps {
                echo "This is the deployment stage"
                // withCredentials([
                //     usernamePassword(credentialId:'server-credential-id', usernameVariable: USER, passwordVariable: PWD)
                // ]){
                //     echo " cred can be used to upload or download from ATF"
                //     sh "some script use ${USER} ${PWD}"
                // }
            }
        }
        // post {
        //     failure{

        //     }
        //     always{

        //     }
        //     success{

        //     }
        // }
    }
}