
pipeline
{
    tools{
        jdk 'myJava'
        maven 'mymaven'
    }
    
    agent any
    stages{
        stage('Clone a repo'){
            steps{
             git 'https://github.com/PAVAN9890/DevOpsClassCodes.git'
            }
        }
        
        stage('compile'){
            steps{
             sh 'mvn compile'
            }
        }
        
        stage('CodeReview'){
            steps{
              sh 'mvn pmd:pmd'
            }
        }
        
        stage('Unitest'){
            steps{
             sh 'mvn test'
            }
        }
        
        stage('Package'){
            steps{
             sh 'mvn package'    
            }
        }
        
        stage('CodeCoverage'){
            steps{
             sh 'mvn cobertura:cobertura -Dcobertura.report.format=xml'    
            }
            
            post{
                success{
                    cobertura autoUpdateHealth: false, autoUpdateStability: false, coberturaReportFile: 'target/site/cobertura/coverage.xml', conditionalCoverageTargets: '70, 0, 0', failUnhealthy: false, failUnstable: false, lineCoverageTargets: '80, 0, 0', maxNumberOfBuilds: 0, methodCoverageTargets: '80, 0, 0', onlyStable: false, sourceEncoding: 'ASCII', zoomCoverageChart: false
                }
            }
        }
    }
    
    
    
}
