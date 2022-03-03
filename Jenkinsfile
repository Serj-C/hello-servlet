pipeline {
    agent any

    stages {
        stage('Git Clone') {
            steps {
                git url: 'https://github.com/Serj-C/hello-servlet.git'
            }
        }

        stage('Gradle Build') {
            tools {
                jdk "JAVA_HOME"
            }
            steps {
                bat 'gradlew build'
            }
        }

        stage('Restart GlassFish') {
            steps {
                bat 'C:\\GlassFish\\glassfish6\\bin\\asadmin.bat list-domains'
                bat 'C:\\GlassFish\\glassfish6\\bin\\asadmin.bat restart-domain domain1'
            }
        }

        stage('Deploy to GlassFish') {
            steps {
                bat 'C:\\GlassFish\\glassfish6\\bin\\asadmin.bat deploy --force=true build/libs/*.war'
                bat 'C:\\GlassFish\\glassfish6\\bin\\asadmin.bat list-applications'
            }
        }
    }
}
