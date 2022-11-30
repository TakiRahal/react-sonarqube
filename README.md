# React && SonarQube

The Best way to Analyze React Project with SonarQube

## Create new Angular Project

    Run npx create-react-app react --template typescript

### Add Script coverage

    script{
        ...
        "coverage": "react-scripts test --coverage",
    }

### Install sonarqube-scanner package

    Run npm install --save-dev sonarqube-scanner
    Run npm install --save-dev jest-sonar-reporter
    
### SonarQube Configuration File

    On the root of the project, create a ‘sonarqube-scanner.js’ file
    
    const scanner = require('sonarqube-scanner');
    scanner(
        {
            serverUrl: "http://localhost:9000",
            options: {
                "sonar.login": "admin",
                "sonar.password": "sonar",
                "sonar.projectName": "react_app",
                "sonar.projectDescription": "Just for demo...",
                "sonar.sourceEncoding":"UTF-8",
                "sonar.sources": "./src",
                "sonar.test.inclusions": "**/*.test.tsx,**/*.test.ts",
                "sonar.exclusions": "**/*.test.tsx",
                "sonar.tests":"./src",
                "sonar.testExecutionReportPaths":"test-report.xml",
                "sonar.javascript.lcov.reportPaths":"coverage/lcov.info"
            },
        },
        () => process.exit()
    );


### Run coverage script

    Run coverage 


### Add sonar script

    script{
        ...
        "test-sonar": "react-scripts test --watchAll=false --coverage --testResultsProcessor jest-sonar-reporter",
        "sonar": "node sonarqube-scanner.js"
    }

### Start SonarQube with Docker

    Run -d --name sonarqube -p 9000:9000 -p 9092:9092 
    
### run sonar script

    Run test-sonar
    Run sonar

## DEMO 
    
[![IMAGE ALT TEXT HERE](https://github.com/TakiRahal/react-sonarqube/blob/main/public/demo-react-sonarqube.png)](https://youtu.be/IiybegzgNuE)
