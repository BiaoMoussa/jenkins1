pipeline {
    agent any

    environment {
        DEPLOY_TO = 'production'
    }
    
    // parameters {
    //     string(name:'NAME', defaultValue:'Biao', description:'Enter your name')
    //     text(name:'DESCRIPTION', defaultValue:'My Name', description:'Enter a description')
    //     booleanParam(name:'MARRIED', defaultValue:true, description:'Are you married?')
    //     choice(name: 'CITY', choices: ['Paris', 'New York', 'Tokyo'], description: 'Select your city')
    //     password(name:'PASSWORD', defaultValue:'', description:'Enter your password')
    // }

    triggers {
        pollSCM('* * * * *')
    }

    

    stages {
        stage('Build'){
            steps {
                
                // echo "NAME : ${NAME}"
                // echo "DESCRIPTION : ${DESCRIPTION}"
                // echo "MARRIED : ${MARRIED}"
                // echo "CITY : ${CITY}"
                // echo "PASSWORD : ${PASSWORD}"

                echo "Building the project..."
            }
        }
        stage('Production') {
            when {
                allOf {
                    branch 'main'
                    environment name: 'DEPLOY_TO', value: 'production'
                }
            }

            input {
                message "Do you want to deploy to production ?"
                ok "Deploy"
                submitter "admin,devops"
                submitterParameter "USER_SUBMIT"
                parameters {
                    string(name: 'VERSION', defaultValue: 'latest', description: 'Enter the version to deploy')
                }

            }
            steps {
                echo "User ${USER_SUBMIT} approved the deployment."
                echo "${VERSION} Deploying to production..."
            }
        }
    }
     
}