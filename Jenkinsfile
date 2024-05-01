pipeline {
 agent {
    node {
        label 'jenkins-agent-1'
    }
 }
 environment {
      versioncheck = ''
 }

//   parameters {
//         // booleanParam, choice, file, text, password, run, or string
//         booleanParam(defaultValue: true, description: '', name: 'booleanExample')
//         string(defaultValue: "TEST", description: 'What environment?', name: 'stringExample')
//         text(defaultValue: "This is a multiline\n text", description: "Multiline Text", name: "textExample")
//         choice(choices: 'US-EAST-1\nUS-WEST-2', description: 'What AWS region?', name: 'choiceExample')
//         password(defaultValue: "Password", description: "Password Parameter", name: "passwordExample")
//     }
//  parameters {
//       choice(choices: 'PROD\nDEV', description: 'Choose PROD or DEV?', name: 'choice')
//  }
   
   options {
                timeout(time: 1, unit: 'HOURS')
                ansiColor('xtrem')
           }
    

    stages {
    //  stage('checkout_from_scm') {
    //  steps {
    //      git branch: 'main', changelog: false, poll: false, url: 'https://github.com/Mygit-Naresh/catalogue.git'
    //    }
    // }
     stage('get version'){
        steps {
         script {
                def jsonfile = readJSON file: 'package.json'
                versioncheck = jsonfile.version
                echo "currentversion is ${versioncheck}"
            }
     }
     }
   
     stage('build the code using') {
        steps {
         sh """
            npm install
         """
        }
     }
}
  post {
   always {
      echo "Check you status below failure or success"
   }
    failure {
        echo "your build failed"
    }
    success {
        echo "your build is success thumbs up"
    }
  }
}

