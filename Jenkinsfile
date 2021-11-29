pipeline { 
    agent any 
    stages { 
        stage ('Checkout') { 
            steps { 
                git branch:'master', url: 'https://github.com/tanyihao/Vulnerable-Web-Application' 
            } 
        } 
         
        stage('Code Quality Check via SonarQube') { 
           steps { 
               script { 
                def scannerHome = tool 'SonarQube'; 
                   withSonarQubeEnv('SonarQube') { 
                   sonar-scanner.bat -D"sonar.projectKey=OWASP" -D"sonar.sources=." -D"sonar.host.url=http://localhost:9000" -D"sonar.login=c1083353f0ec061772eafeefda7fd485407e98db"

                   } 
               } 
           } 
        } 
    } 
    post { 
        always { 
            recordIssues enabledForFailure: true, tool: sonarQube() 
        } 
    } 
} 
