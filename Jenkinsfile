pipeline {
    agent any

    // parameters {
    //     booleanParam(name:'DEPLOY_TO', defaultValue:true, description:'Deploy to production environment')
    //     string(name: 'VERSION', defaultValue: '1.0.0', description: 'Enter the version to deploy')
    // }




    
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

    tools {
        gradle 'Gradle9.5.0'
    }
    

    stages {
    
        stage('Show gradle version') {
            steps {
                sh 'gradle --version'
            }
        }

        stage('Build App') {
            failFast true
            parallel{
                stage('Build Frontend'){
                    steps {
                
                // echo "NAME : ${NAME}"
                // echo "DESCRIPTION : ${DESCRIPTION}"
                // echo "MARRIED : ${MARRIED}"
                // echo "CITY : ${CITY}"
                // echo "PASSWORD : ${PASSWORD}"

                echo "Building the frontend..."
                    }
                }
                stage('Build Backend'){
                    steps {
                        echo "Building the backend..."
                        sh "echo Building the backend... > build.log"
                        archiveArtifacts(artifacts: 'build.log')
                    }
                }
            }
        }

        // stage('Testing') {
        //     matrix {
        //         axes {
        //             axis {
        //                 name 'PLATEFORM'
        //                 values 'Windows', 'Linux', 'MacOS'
        //             }
        //             axis {
        //                 name 'BROWSER'
        //                 values 'Chrome', 'Firefox', 'Safari'
        //             }
        //         }

        //         stages {
        //             stage('Run Platform test') {
        //                 steps {
        //                     echo "Running tests on ${PLATEFORM} ..."
        //                 }
        //             }

        //             stage('Run Browser test') {
        //                 steps {
        //                     echo "Running tests on browser  ${BROWSER}..."
        //                 }
        //             }
        //         }
        //     }
        // }

       
        stage('Go to production'){ 
            // when {
            //     allOf {
            //         branch 'main'
            //         equals expected: 'production', actual: params.DEPLOY_TO
            //     }
            // }

            input {
                message "Do you want to deploy to production ?"
                ok "Deploy"
                submitter "admin,devops"
                submitterParameter "USER_SUBMIT" 
            }
            steps {
                echo "User ${USER_SUBMIT} approved the deployment."
                // echo "${VERSION} Deploying to production..."
            }
        }
    }
     
}
