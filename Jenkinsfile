pipeline {
   agent any
   environment{
      path="C:\\Windows\\System32"
      EMAIL_TO = 'sravani055@gmail.com'
   }
    
    stages {
                
       stage('Build') {
         steps {
             bat 'C:\\Windows\\Microsoft.NET\\Framework64\\v4.0.30319\\MSBuild.exe TestBuild.sln /p:VisualStudioVersion=10.0 /p:Configuration=Release /m:5 /t:Rebuild'
            // bat 'C:/Program Files (x86)/Microsoft Visual Studio/2017/BuildTools/MSBuild/15.0/Bin/MSBuild.exe TestBuild.sln /p:VisualStudioVersion=10.0 /p:Configuration=Release /t:Rebuild'
             //bat  """ "C:\\Program Files (x86)\\Microsoft Visual Studio\\2017\\BuildTools\\MSBuild\\15.0\\Bin\\MSBuild.exe" Demo_v2.sln /p:Configuration=Release /t:Rebuild """
             //bat  """ "C:\\Program Files (x86)\\Microsoft Visual Studio\\2017\\BuildTools\\MSBuild\\15.0\\Bin\\MSBuild.exe" "C:\\windows\\system32\\config\\systemprofile\\AppData\\Local\\Jenkins.jenkins\\workspace\\clone_demo\\Demo_v2.sln" /p:Configuration=Release /t:Rebuild """
              // bat """ "C:/Program Files (x86)/Microsoft Visual Studio/2017/Professional/MSBuild/15.0/Bin/MSBuild.exe" "C:\\windows\\system32\\config\\systemprofile\\AppData\\Local\\Jenkins.jenkins\\workspace\\clone_demo\\Demo_v2.sln" /p:Configuration=Release /t:Rebuild """

             echo "Entered into Build"

        }
     }
    }
post {
       failure {
            emailext body: 'Check console output at $BUILD_URL to view the results. \n\n ${CHANGES} \n\n -------------------------------------------------- \n${BUILD_LOG, maxLines=100, escapeHtml=false}', 
                    to: "${EMAIL_TO}", 
                    subject: 'Build failed in Jenkins: $PROJECT_NAME - #$BUILD_NUMBER'
        }
        unstable {
            emailext body: 'Check console output at $BUILD_URL to view the results. \n\n ${CHANGES} \n\n -------------------------------------------------- \n${BUILD_LOG, maxLines=100, escapeHtml=false}', 
                    to: "${EMAIL_TO}", 
                    subject: 'Unstable build in Jenkins: $PROJECT_NAME - #$BUILD_NUMBER'
        }
        changed {
            emailext body: 'Check console output at $BUILD_URL to view the results.', 
                    to: "${EMAIL_TO}", 
                    subject: 'Jenkins build is back to normal: $PROJECT_NAME - #$BUILD_NUMBER'
        }
    }
    }

}
