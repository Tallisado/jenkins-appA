#!groovy

// dockerNode {
//    stage("Checkout"){
//         // Checkout code from repository
//         echo "setting properties"
//         //properties([$class: PipelineTriggersJobProperty([[$class: 'GitHubPushTrigger'], pollSCM('H/15 * * * *')])])
//         checkout scm
//     }
//    stage("Build"){
//
//         def mvnHome = tool 'M3'
//         //echo "${mvnHome}/bin:${env.PATH}"
//         env.PATH = "${mvnHome}/bin:${env.PATH}" //Do I need this?
//         // Run the maven build
//         "run maven"
//         sh "mvn clean install"
//         step([$class: 'ArtifactArchiver', allowEmptyArchive: true, artifacts: '**/target/*.jar', fingerprint: true])
//         step([$class: 'JUnitResultArchiver', testResults: '**/target/surefire-reports/TEST-*.xml'])
//    }
// }

dockerNode(image: "maven:3.3.3-jdk-8", sideContainers: ["selenium/standalone-firefox"]) {
  git "https://github.com/wakaleo/game-of-life"
  sh 'mvn clean test'
}
