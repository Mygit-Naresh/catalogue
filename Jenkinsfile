pipeline {
 agent any
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
 parameters {
      choice(choices: 'PROD\nDEV', description: 'Choose PROD or DEV?', name: 'choice')
 }
   
   options {
                timeout(time: 1, unit: 'HOURS') 
                disableConcurrentBuilds()
   }            ansiColor('xtrem')

    stages {
   
     stage('get version'){
        script {
        def jsonfile = readJSON file: 'package.json'
                versioncheck = jsonfile.version
                echo "currentversion is ${versioncheck}"
            }
     }
     stage('checkout_from_scm') {
    //   when {
    //     expression { environment == "PROD" }

    // }
       steps {
         git branch: 'main', changelog: false, poll: false, url: 'https://github.com/Mygit-Naresh/catalogue.git'
       }
     
}
     stage('DEV') {
        steps {
     echo "${DEV}"
        }
     }
}
  post {
   always {
      echo "final execution"
   }
    failure {
        echo "your build failed"
    }
    success {
        echo "your build is success thumbs up"
    }
  }
}

