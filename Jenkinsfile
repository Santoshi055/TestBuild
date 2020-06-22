pipeline {
   agent any
   environment{
      path="C:\\Windows\\System32"
   }
     notifyStarted()
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

def notifyStarted() {
  // send to Slack
  slackSend (color: '#FFFF00', message: "STARTED: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]' (${env.BUILD_URL})")

  // send to HipChat
  hipchatSend (color: 'YELLOW', notify: true,
      message: "STARTED: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]' (${env.BUILD_URL})"
    )

  // send to email
  emailext (
      subject: "STARTED: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]'",
      body: """<p>STARTED: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]':</p>
        <p>Check console output at &QUOT;<a href='${env.BUILD_URL}'>${env.JOB_NAME} [${env.BUILD_NUMBER}]</a>&QUOT;</p>""",
      recipientProviders: [[$class: 'DevelopersRecipientProvider']]
    )
}
}
