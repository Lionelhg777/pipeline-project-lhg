pipeline {
    agent any

    stages {
        stage('Get Code GitHub') {
            steps {
                // Get some code from a GitHub repository
                git 'https://github.com/Lionelhg777/maven-project-lhg.git'              
            }
        }
        stage('Compilation') {
            steps {
                // To run Maven on a Windows agent, use
                bat "mvn clean package checkstyle:checkstyle"              
            }
        }
        stage('Deploy Tomcat') {
            steps {
                // Stop Tomcat 
                bat "C:\\Users\\ljhernandez\\Desktop\\formacion_Jenkins\\apache-tomcat-8.5.78\\bin\\shutdown.bat"
                sleep 30
                
                // Clean webapp Tomcat (old version)
                bat "del C:\\Users\\ljhernandez\\Desktop\\formacion_Jenkins\\apache-tomcat-8.5.78\\webapps\\webapp.war"
                
                // Deploy webapp (new version)
                bat "copy C:\\ProgramData\\Jenkins\\.jenkins\\workspace\\hhh\\webapp\\target\\webapp.war C:\\Users\\ljhernandez\\Desktop\\formacion_Jenkins\\apache-tomcat-8.5.78\\webapps\\webapp.war"
                sleep 30
   
                // Start Tomcat
                bat "C:\\Users\\ljhernandez\\Desktop\\formacion_Jenkins\\apache-tomcat-8.5.78\\bin\\startup.bat"
            }
        }
    }
}
