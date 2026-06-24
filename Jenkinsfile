pipeline {
    agent {
        docker
        { 
            image 'mcr.microsoft.com/playwright:v1.59.1-noble'
            args '-u=root --entrypoint='
        }  
        
    }

    parameters {
        booleanParam(name: 'All_Test', defaultValue: false, description: 'Lancer tous tests')

        choice(name: 'Navigateur', choices: ['chrome', 'firefox', 'webkit', 'chromium'], description: 'Choisir l\'environnement')

        choice(name: 'Tags', choices: ['@E2E', '@Smoke', '@Valid'], description: 'Choisir le tag')

    }


    stages {


        stage('Installation des dependances') {
            steps {
                sh 'npm install'
            }
        }

        stage('Lancer le test') {

            steps {
                    sh 'npx playwright test'

                script {
            
                    // if(params.All_Test) {
                    //     sh 'npx playwright test'
                    //     echo "Test reussi !"
                    // } else {
                    //     sh 'npx playwright test --grep '+ params.Navigateur + ' --project='+  params.Tags
                    //     echo "Test reussi !"
                    // }
                }
            }
        }
    }
}
