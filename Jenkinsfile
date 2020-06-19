pipeline {
   agent any
   environment{
      path="C:\\Windows\\System32"
   }
    stages {
                
      stage('Build') {
         steps {
             bat 'dir'
           	  bat 'C:\\Windows\\Microsoft.NET\\Framework64\\v4.0.30319\\MSBuild.exe TestBuild.sln /p:Configuration=Release /t:Rebuild'
            //bat """ "C:\\Program Files (x86)\\Microsoft Visual Studio\\2017\\BuildTools\\MSBuild\\15.0\\Bin\\MSBuild.exe" TestBuild.sln /tv:15.0 /p:Configuration=Release /t:Rebuild """
           	// bat  """ "C:\\Program Files (x86)\\Microsoft Visual Studio\\2017\\BuildTools\\MSBuild\\15.0\\Bin\\MSBuild.exe" TestBuild.sln /p:Configuration=Release /t:Rebuild """
        	 //  bat  """ "C:\\Program Files (x86)\\Microsoft Visual Studio\\2017\\BuildTools\\MSBuild\\15.0\\Bin\\MSBuild.exe" "C:\\Windows\\System32\\config\\systemprofile\\AppData\\Local\\Jenkins.jenkins\\workspace\\TestBuild\\TestBuild.sln" /p:Configuration=Release /t:Rebuild """
              // bat """ "C:/Program Files (x86)/Microsoft Visual Studio/2017/Professional/MSBuild/15.0/Bin/MSBuild.exe" "C:\\windows\\system32\\config\\systemprofile\\AppData\\Local\\Jenkins.jenkins\\workspace\\TestBuild\\TestBuild.sln" /p:Configuration=Release /t:Rebuild """
               
               bat "msbuild ./TestBuild/TestBuild.csproj"
             echo "Entered into Build"
        }
      }
    }
     
}
