pipeline{
    agent{
        label 'jenkins-agent-docker-jnlp'
    }
    environment{
        staging_server="185.27.134.119"
    }
    stages{
        stage('Deploy to Remote'){
            steps{
                sh '''
                    for fileName in `find ${WORKSPACE} -type f -mmin -10 | grep -v ".git" | grep -v "Jenkinsfile"`
                    do
                        fil=$(echo ${fileName} | sed 's/'"${JOB_NAME}"'/ /' | awk {'print $2'})
                        scp -r ${WORKSPACE}${fil} root@${staging_server}:/var/www/html/mbaquatech${fil}
                    done
                '''
            }
        }
    }
}