
node {
   def mvnHome
   //def folderName="javadoctest"
   //def projectFolderName="Demo pipeline"
   
   //selectedJob(projectFolderName + folderName)
   //shell('pwd')
   //shell('ls -la')
   
   stage('Preparation') { // for display purposes
      // Get some code from a GitHub repository
      git 'https://github.com/urestisandra/hello-world.git'
      // Get the Maven tool.
      // ** NOTE: This 'M3' Maven tool must be configured
      // **       in the global configuration.           
      mvnHome = tool 'Maven 3.5.0'
   }
   stage('Build') {
      // Run the maven build
      //sh cd "/var/lib/jenkins/workspace/Demo pipeline/javadoctest"
      if (isUnix()) {
         //sh "'${mvnHome}/bin/mvn' -Dmaven.test.failure.ignore clean package"
         sh "'${mvnHome}/bin/mvn' -Dmaven.test.skip=true clean package"
      } else {
         //bat(/"${mvnHome}\bin\mvn" -Dmaven.test.failure.ignore clean package/)
         bat(/"${mvnHome}\bin\mvn" -Dmaven.test.skip=true clean package/)
      }
   }
   stage('Results') {
      //junit '**/target/surefire-reports/TEST-*.xml'
      junit '**/target/TEST-*.xml'
      archive 'target/*.jar'
   }
}
