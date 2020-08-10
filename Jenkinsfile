pipeline {
   agent any
   environment{
      path="C:\\Windows\\System32"
   }
    
    stages {
                
       stage('Build') {
         steps {
            bat 'C:\\Windows\\Microsoft.NET\\Framework64\\v4.0.30319\\MSBuild.exe "C:\windows\system32\config\systemprofile\AppData\Local\Jenkins.jenkins\workspace\TestBuild\TestBuildTestBuild.csproj" /p:VisualStudioVersion=10.0 /T:Clean /p:Configuration=Release /p:OutputPath="obj/Release" /p:PrecompileBeforePublish=true /t:Rebuild /p:PublishProfile=FolderProfile'
            echo "Entered into Build"

        }
     }
        stage("Prepare artifacts"){
           steps{
              
            fileOperations([fileDeleteOperation(excludes: '', includes: '**/*.pdb'),
                            fileDeleteOperation(excludes: '', includes: '**/*.config'), 
                folderCreateOperation('C:\\Windows\\System32\\config\\systemprofile\\AppData\\Local\\Jenkins.jenkins\\workspace\\TestBuild\\Publish'),
                folderCopyOperation(destinationFolderPath: 'C:\\Windows\\System32\\config\\systemprofile\\AppData\\Local\\Jenkins.jenkins\\workspace\\TestBuild\\Publish' ,sourceFolderPath: 'C:\\Windows\\System32\\config\\systemprofile\\AppData\\Local\\Jenkins.jenkins\\workspace\\TestBuild\\TestBuild\\bin\\Release'), 
                fileZipOperation(folderPath: 'C:\\Windows\\System32\\config\\systemprofile\\AppData\\Local\\Jenkins.jenkins\\workspace\\TestBuild\\Publish', outputFolderPath: 'C:\\Windows\\System32\\config\\systemprofile\\AppData\\Local\\Jenkins.jenkins\\workspace\\TestBuild')])
                           }
        }
        stage('Archive artifacts'){
           steps{
          archiveArtifacts 'Publish.zip'
           }
        }
        stage ('Upload file') {
            steps {
                rtUpload (
                    serverId: 'Artifactory-Version-4.15.0', // Obtain an Artifactory server instance, defined in Jenkins --> Manage:
                    spec: """{
                            "files": [
                                    {
                                        "pattern": "Publish.zip",
                                        "target": "Jenkins-integration/"
                                    }
                                ]
                            }"""
                )
            }
        }
        stage ('Publish build info') {
            steps {
                rtPublishBuildInfo (
                    serverId: 'Artifactory-Version-4.15.0'
                )
            }
        }
    }
              
/*post {
        always {
           //emailext body: 'Check console output at $BUILD_URL to view the results.', subject: 'Jenkins build is back to normal: $PROJECT_NAME - #$BUILD_NUMBER',to:'sravani055@gmail.com,ravikiran.geddam@gmail.com'
     
        }
    }*/
    

}
