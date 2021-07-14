pipeline{
    agent any
    parameters{
        choice(name: 'VERSION', choices: ['1.1.0', '1.2.0'], description:'')
        booleanParam(name: 'executeTests', defaultValue: true, description:'')
    }
    stages {
        stage("build"){
            steps {
                echo "This is the build step"
            }
        }

        stage("test") {
            when {
                expression {
                    params.executeTests == true
                }
            }
            steps {
                echo "This is the test step"
            }
        }

        stage("deploy") {
            steps {
                echo "The current version selected is ${params.VERSION}"
                echo "This is the deployment stage"
            }
        }
    }
}
