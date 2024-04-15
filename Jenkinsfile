pipeline {
    agent any
    
    environment {
        PLAYWRIGHT_IMAGE = 'mcr.microsoft.com/playwright:v1.42.1-jammy'
    }
    
    stages {
        stage('Install and Test with Playwright') {
            steps {
                script {
                    // Execute o contêiner Docker com o script
                    docker.image(PLAYWRIGHT_IMAGE).inside("-it --rm -v ${WORKSPACE}:/test") {
                        // Instale as dependências
                        sh 'npm install'
                        
                        // Execute os testes
                        sh 'npx playwright test'
                    }
                }
            }
        }
    }
}
