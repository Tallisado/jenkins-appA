#!groovy

dockerNode(image: "maven:3.3.3-jdk-8") {
  stage("Checkout SCM"){
    checkout scm
  }
  stage("Unit Testing"){
    sh 'mvn clean test'
  }
  stage("Deploy"){
    sh 'mvn clean install '
    step([$class: 'ArtifactArchiver', allowEmptyArchive: true, artifacts: '**/*.jar', fingerprint: true])
    //step([$class: 'JUnitResultArchiver', testResults: '**/target/surefire-reports/TEST-*.xml'])
  }
  // stage("Coverage"){
  //   /step([$class: 'JacocoPublisher', execPattern: 'target/coverage-reports/jacoco.exec'])
  // }
  // stage('Analysis') {
  //    sh "mvn -Dpmd.failOnViolation=false -Dcpd.failOnViolation=false -Dfindbugs.failOnError=false pmd:check pmd:cpd-check"
  //    step([$class: 'PmdPublisher', pattern: 'target/pmd.xml'])
  //    step([$class: 'DryPublisher', pattern: 'target/cpd.xml'])
  //    step([$class: 'TasksPublisher', high: 'FIXME', low: '', normal: 'TODO', pattern: 'src/**/*.java'])
  // }
}
