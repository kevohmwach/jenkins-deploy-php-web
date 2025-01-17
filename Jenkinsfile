pipeline{
    agent { 
        node {
            label 'jenkins-agent-docker-jnlp'
        }
      }
    triggers {
        pollSCM '*/5 * * * *'
    }
    environment{
        staging_server="185.27.134.119"
        FTP_CREDENTIALS = credentials('GradestarFTP_credentials')
        FTP_HOST_NAME = credentials('Gradestar_ftp_hostname')
        
    }
    stages{
        stage('Deploy to Remote'){
            steps{
                sh '''
                    echo ${FTP_HOST_NAME}
                    /usr/bin/git-ftp init --user ${FTP_CREDENTIALS_USR} --passwd ${FTP_CREDENTIALS_PSW} ftp://${FTP_HOST_NAME}/public_html/
                '''
            }
        }
    }
}


//git ftp init --user ${FTP_CREDENTIALS_USR} --passwd ${FTP_CREDENTIALS_PSW} ftp://${FTP_HOST_NAME}/public_html/
//git ftp init --user $FTP_USERNAME --passwd $FTP_PASSWORD ftp://${staging_server}/public_html/

// sh '''
//                     for fileName in `find ${WORKSPACE} -type f -mmin -10 | grep -v ".git" | grep -v "Jenkinsfile"`
//                     do
//                         fil=$(echo ${fileName} | sed 's/'"${JOB_NAME}"'/ /' | awk {'print $2'})
//                         scp -r ${WORKSPACE}${fil} root@${staging_server}:/var/www/html/mbaquatech${fil}
//                     done
//                 '''