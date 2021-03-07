pipeline {
    agent { any } 
    stages {
        stage('Source Code Management') {
            steps {
                git 'https://github.com/spring-projects/spring-petclinic.git'
            }
            
        }
        stage('Maven Build') {
            steps {
                sh 'mvn clean package'
            }
            
        }
        
         stage('Ansible Deploy') {
            steps {
                sshPublisher(publishers: [sshPublisherDesc(configName: 'private_server', transfers: [sshTransfer(cleanRemote: false, excludes: '', execCommand: 'ansible-playbook Playbook.yml', execTimeout: 120000, flatten: false, makeEmptyDirs: false, noDefaultExcludes: false, patternSeparator: '[, ]+', remoteDirectory: '', remoteDirectorySDF: false, removePrefix: 'webapp', sourceFiles: 'webapp/*.war')], usePromotionTimestamp: false, useWorkspaceInPromotion: false, verbose: false)])
            }
         }
        
    }
}
