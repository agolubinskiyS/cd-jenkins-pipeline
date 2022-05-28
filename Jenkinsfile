@Library('cd-shared-library') _


String branchName = "master"
String gitCredentials = "git-credentials-s"
String repoUrl = "https://github.com/agolubinskiyS/cd-jenkins-pipeline.git"
node('cloner'){
    stage('GIT') {
        // Clones the repository from the current branch name
        echo 'Make the output directory'
        sh 'mkdir -p build'
        sh("pwd")
        sh("ls -lha")
    
        echo 'Cloning files from (branch: "' + branchName + '" )'
        dir('build') {
            git branch: branchName, credentialsId: 	gitCredentials, url: repoUrl
            sh("pwd")
            sh("ls -lha")

        }
    } 
}  



// params = [url: 'https://mi-url.com', tenant: 's000004', deploymentDescriptor: DEPLOYMENTDESCRIPTOR, model: 'basic', version: '11.0.1', service: 'grafana-eos']

def DEV = {
    // sh("echo $DEPLOYMENTDESCRIPTOR")
    params = [url: 'https://mi-url.com', tenant: 's000004', model: 'basic', version: '11.0.1', service: 'grafana-eos']
    doCD(params)

}

DEV.call()



