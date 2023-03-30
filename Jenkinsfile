pipeline{
    agent any
    stages{
        stage("checkout"){
            steps{
                git branch: 'main', url: 'https://github.com/gopikrishna7/Nodeapp.git'
                echo "Checkout completed"
                echo "########################################################################"
            }
        }
        // stage("build"){
        //     steps{
        //         nodejs('Node'){
        //             sh "npm install"
        //         }
        //     }
        // }
        // stage("test"){
        //     steps{
        //         nodejs('Node'){
        //             sh "npm test"
        //         }
        //     }
        // }
        // stage("Sonarscan"){
        //     environment{
        //         scannerHome = tool 'sonar-scanner'
        //     }
        //     steps{
        //         withSonarQubeEnv(installationName:'sq1'){
        //             sh "${scannerHome}/bin/sonar-scanner"
        //         }
        //         timeout(time:5,unit:'MINUTES'){
        //             waitForQualityGate abortPipeline: true

        //         }
        //     }
        // }
        // stage('DockerBuild'){
        //     steps{
        //         sh "docker build -t mynodeimg ."
        //     }     
        // }
        // stage("Scan Image"){
        //     steps{
        //         //sh "trivy image --no-progress --exit-code 1 --severity HIGH,CRITICAL mynodeimg"
        //         sh "trivy image mynodeimg"
        //     }
        // }
        // stage("Docker push"){
        //     environment{
        //         SERVER_CRED=credentials('DockerHub')
        //     }
        //     steps{
        //         sh 'echo ${SERVER_CRED_PSW} | docker login -u ${SERVER_CRED_USR} --password-stdin'
        //         sh "docker tag mynodeimg gopikrishna99899/mynodeimg"
        //         sh "docker push gopikrishna99899/mynodeimg"
        //     }
        // }
        stage("version"){
            steps{
                script{
                    def packageJSON = readJSON file: 'package.json'
                    def packageJSONVersion = packageJSON.version
                    echo packageJSONVersion

                }
            }
            

        }
        // stage("KubernetesDeploy"){
        //     steps{
        //         script{
        //             def manifest = readFile('kubernetes/Deployment.yaml')
        //             manifest = manifest.replaceAll('image:.*', "image: gopikrishna99899/mynodeimg")
        //             // sh "echo '${manifest}' | kubectl apply -f -"
        //             //sh "echo '${manifest}' > kubernetes/Deployment.yaml"
        //             sh "helm install myapp helm"

        //         }
        //         // sh "kubectl apply -f kubernetes"
        //     }
        // }
    }
    // post{
    //     always{
    //             sh 'docker logout'
    //     }
    // }

}