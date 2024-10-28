pipeline {
    agent any
    tools {
        nodejs 'node-latest'
    }

    stages {
        // stage('Get Code') {
        //     steps {
        //         echo  "Getting code from github..."
        //         git 'https://github.com/sexymanalive/reactjs-devop8-template'
        //         sh 'ls -lrt'
        //     }
        // }


        stage("Run Tests"){
            steps {

                script{
                    if (params.RUN_TEST){
                        sh """
                        echo "Install dependencies " 
                        npm install 
                        echo "Running Unit Test..."
                        npm test
                        
                        """
                    }else {
                        sh "echo 'Unit Test will NOT run  ' "
                    }
                }
            }
        }

        stage("Build and Deploy"){
            steps{
                echo "Using docker compose to build and deploy "
                sh """
                    docker compose up -d
                """
            }
        }

        stage("Add domain name"){
            steps{
                echo "Run shellscript to add domain "
                // sh """
                // sudo bash /home/keo/utilities/adddomainssl.sh  new-reactjs  3000
                // """
            }
        }
    }

    post{
        // this will clean our workspace directory even it success or fail
        always{
            cleanWs()
        }
    }
}