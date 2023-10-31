/*ForWindowsusers;RequirestheDockerPipelineplugin*/ 
pipeline{
  agent any 
  stages{
    stage('build'){
      steps{
        script{
          /*thereturnvaluegetscaughtandsavedintothevariable MY_CONTAINER*/
          MY_CONTAINER=bat(script:'@dockerrun-d-i maven:3.9.4-eclipse-temurin-17-alpine',returnStdout:true).trim() echo"mycontainer_idis${MY_CONTAINER}"
          /*python--versiongetsexecutedinsidetheContainer*/ bat"dockerexec${MY_CONTAINER}mvn--version"
          /*theContainergetsremoved*/
          bat"dockerrm-f${MY_CONTAINER}"
        }
      }
    }
  }
}
