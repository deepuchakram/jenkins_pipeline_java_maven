node {
   // Mark the code checkout 'stage'....
   stage 'Checkout'
   
   git url: 'https://github.com/TTFHW/jenkins_pipeline_java_maven.git'

   // Get the maven tool.
   // ** NOTE: This 'M3' maven tool must be configured
   // **       in the global configuration.           
   def mvnHome = tool 'Maven'

   // Mark the code build 'stage'....
   stage 'Build'
   // Run the maven build
   shell "${mvnHome}/bin/mvn -Dmaven.test.failure.ignore clean package"
   shell 'ln -s tests/test-results-unit.xml $WORKSPACE'
  junit "test-results-unit.xml"
  step([$class: 'JUnitResultArchiver', testResults: '**/target/surefire-reports/TEST-*.xml'])
}
