pipeline {

  agent any

  parameters {
    booleanParam(name: 'executeTests', defaultValue: true, description: '')
  }

  stages {

    stage("build") {
      step {
        echo 'building the application...'
      }
    }

    stage("test") {
      when {
        expressions {
          params.executeTests
        }
      }
      step {
        echo 'testing the application...'
      }
    }

    stage("deploy") {
      input {
        message "Select the environment to deploy to"
        ok "Done"
        parameters {
          choice(name: 'ENV', choices: ['dev','staging','prod'], description: '')
        }
      }

      step {
        echo "deploying to ${ENV}"
      }
    }

  }

}
