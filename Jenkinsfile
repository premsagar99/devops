pipeline {
    agent any

parameters {

           
//         choice choices: ['Component','App'], name: 'Type',  description: 'Select the type'
//         extendedChoice defaultValue: 'Vtune,Inspector,Advisor', multiSelectDelimiter: ',', name: 'Test', quoteValue: false, saveJSONParameterToFile: false, type: 'PT_CHECKBOX', value: 'Vtune,Inspector,Advisor', visibleItemCount: 4
           
        choice choices: ['Build', 'Test','Logs'], name: 'BUILDTYPE',  description: 'Type of the build'
        extendedChoice defaultValue: 'Unit Test,Functional Test', multiSelectDelimiter: ',', name: 'Test', quoteValue: false, saveJSONParameterToFile: false, type: 'PT_CHECKBOX', value: 'Unit Test,Functional Test'
}
stages {
          
           stage("checkout code") {
             when { expression { params.BUILDTYPE == 'Build'  }  }
             steps {
              println "\033[34m............checkout code..............\033[0m"
              echo "checkout code"
             }
           }
           stage("select build VM and Build") {
             when { expression { params.BUILDTYPE == 'Test' ||  params.BUILDTYPE == 'Build'  }  }
             steps {
              println "\033[34m............select build VM and Build..............\033[0m"
              echo "select build VM and Build"
             }
           }
           stage("unit testing") {
            when { expression { params.BUILDTYPE == 'Test' ||  params.BUILDTYPE == 'Build'  }  }
            steps {
                println "\033[34m............unit testing..............\033[0m"
                echo "unit testing"
            }
           }  
           stage("Static Analysis tools (Sonarqube)") {
            when { expression { params.BUILDTYPE == 'Test' ||  params.BUILDTYPE == 'Build'  }  }
            steps {
                println "\033[34m............Static Analysis tools (Sonarqube)..............\033[0m"
                echo "Static Analysis tools (Sonarqube)"
            }
           } 
           stage("assess and report the results") {
            when { expression { params.BUILDTYPE == 'Logs' ||  params.BUILDTYPE == 'Build'  }  }
            steps {
                println "\033[34m............assess and report the results..............\033[0m"
                echo "assess and report the results"
            }
           } 
           stage("publish the results") {
            when { expression { params.BUILDTYPE == 'Logs' ||  params.BUILDTYPE == 'Build'  }  }
            steps {
                println "\033[34m............publish the results..............\033[0m"
                echo "publish the results"
            }
           } 
           stage("merge check") {
            when { expression { params.BUILDTYPE == 'Build'  }  }
            steps {
                println "\033[34m............merge check..............\033[0m"
                echo "merge check"
            }
           } 
           stage("post merge hook") {
            when { expression { params.BUILDTYPE == 'Build'  }  }
            steps {
                println "\033[34m............post merge hook..............\033[0m"
                echo "post merge hook"
            }
           } 
           stage("build") {
            when { expression { params.BUILDTYPE == 'Build'  }  }
            steps {
                println "\033[34m............build..............\033[0m"
                echo "build"
            }
           } 
           stage("test env") {
            when { expression { params.BUILDTYPE == 'Build'  }  }
            steps {
                println "\033[34m............test env..............\033[0m"
                echo "test env"
            }
           } 
           stage("static analysis tools(sonar qube)") {
            when { expression { params.BUILDTYPE == 'Build' || params.BUILDTYPE == 'Test'  }  }
            steps {
                println "\033[34m............Dropping the artifacts..............\033[0m"
                echo "Publishing the app"
            }
           } 
 
           stage("publishing the results") {
            when { expression { params.BUILDTYPE == 'Build' || params.BUILDTYPE == 'Test' || params.BUILDTYPE == 'Logs'  }  }
            steps {
                println "\033[34m............publish the results..............\033[0m"
                echo "publish the results"
            }
           } 
           stage("drop ready") {
            when { expression { params.BUILDTYPE == 'Build' }  }
            steps {
                println "\033[34m............drop ready..............\033[0m"
                echo "drop ready"
            }
           } 
           stage("drop to artifactory") {
            when { expression { params.BUILDTYPE == 'Build' }  }
            steps {
                println "\033[34m............drop to artifactory..............\033[0m"
                echo "drop to artifactory"
            }
           } 
           stage("reset/clean VM") {
            when { expression { params.BUILDTYPE == 'Build' }  }
            steps {
                println "\033[34m............Dropping the artifacts..............\033[0m"
                echo "reset/clean VM"
            }
           } 
  

        } 
}
