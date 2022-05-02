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



DEPLOYMENTDESCRIPTOR = '''
{
    \\"general\\": {
        \\"serviceId\\": \\"s000004/s000004-grafana-prueba\\",
        \\"appname\\": \\"grafana-prueba\\",
        \\"grafanaAdminUser\\": \\"admin\\",
        \\"identity\\": {
            \\"approlename\\": \\"s000004\\"
        },
        \\"network\\": {
            \\"networkName\\": \\"s000004-core\\"
        },
        \\"resources\\": {
            \\"INSTANCES\\": 1,
            \\"CPUs\\": 1,
            \\"MEM\\": 1024
        }
    },
    \\"settings\\": {
        \\"logs\\": {
            \\"nginxLogLevel\\": \\"error\\"
        }
    },
    \\"placement\\": {
        \\"marathonConstraintSection\\": {
            \\"marathonConstraintName\\": \\"\\",
            \\"marathonConstraintOperator\\": \\"\\",
            \\"marathonConstraintValue\\": \\"\\"
        }
    },
    \\"environment\\": {
        \\"grafanaConsulDomain\\": \\"\\",
        \\"grafanaSSOURI\\": \\"\\",
        \\"vault\\": {
            \\"vaultHosts\\": \\"vault.service.eos.yankee.labs.stratio.com\\",
            \\"vaultPort\\": 8200
        }
    }
}'''.stripMargin().stripIndent()




// params = [url: 'https://mi-url.com', tenant: 's000004', deploymentDescriptor: DEPLOYMENTDESCRIPTOR, model: 'basic', version: '11.0.1', service: 'grafana-eos']

params = [url: 'mi-url.com', tenant: 's000004', model: 'basic', version: '11.0.1', service: 'grafana-eos']

doCD(params)

