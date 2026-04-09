pipline {
    agent any

    // Paramètres de la pipeline
    parameters {
        string(name:'NAME', defaultValue:'Biao', description:'Enter your name')
        text(name:'DESCRIPTION', defaultValue:'My Name', description:'Enter a description')
        booleanParam(name:'MARRIED', defaultValue:true, description:'Are you married?')
        choice(name: 'CITY', choices: ['Paris', 'New York', 'Tokyo'], description: 'Select your city')
        password(name:'PASSWORD', defaultValue:'', description:'Enter your password')
    }

    stages {
        stage('Build'){
            steps {
                echo 'NAME : ${ NAME }'
                echo 'DESCRIPTION : ${ DESCRIPTION }'
                echo 'MARRIED : ${ MARRIED }'
                echo 'CITY : ${ CITY }'
                echo 'PASSWORD : ${ PASSWORD }'
            }
        }
    }
}
