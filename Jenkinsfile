node ('appserver-jenkins_agent'){  
    def app
    stage('Cloning Git') {
        /* Let's make sure we have the repository cloned to our workspace */
       checkout scm
    }  
/*    stage('SAST'){
        build 'SECURITY-SAST-SNYK'
    } */

    
    stage('Build-and-Tag') {
        
    /* This builds the actual image; synonymous to
         * docker build on the command line */
        app = docker.build("keshavkumar2021/snake")
    }
    stage('Post-to-dockerhub') {
        sh 'echo Post-to-Dockerhub'
    
    docker.withRegistry('https://registry.hub.docker.com', 'Docker') {
           app.push("latest")
       			}
         }
 /*   stage('SECURITY-IMAGE-SCANNER'){
        build 'SECURITY-IMAGE-SCANNER-AQUAMICROSCANNER'
    } */
  
    
    stage('Pull-image-server') {
        sh 'echo pullimageserver'
    
         sh "docker-compose down"
         sh "docker-compose up -d"	
      }
    
 /*   stage('DAST')
        {
        build 'SECURITY-DAST-OWASP_ZAP'
        } */
 
}
