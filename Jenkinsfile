node {
    def response
withCredentials([usernamePassword(credentialsId: 'gitlab', usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')]) {
  sh '''
  echo $PASSWORD
  echo USERNAME
  echo "username is $USERNAME"
  '''
  response = sh (script: "curl -s -XGET -H 'Content-Type: application/json' --header 'PRIVATE-TOKEN: glpat-Ce5D9a98_1PeoYt3SyJ8' https://gitlab.com/api/v4/projects/rnd17%2Fnewtest | jq -r '.id'", returnStdout: true)
  
sh '''
echo "Repo ID is"
             echo '''+response+'''
             '''
}
sh '''
   #!/bin/bash
    echo "Repo ID is again"
             IDN=`echo '''+response+'''`
             echo "ID is $IDN"
    echo "$USERNAME is my name"
'''
 
//     def config = new ConfigSlurper().parse(new File('config.groovy').toURL())
// assert ['name'] == config.flatten().keySet().collect {it as String} 
//     for (String name: config.flatten().keySet()) {
//     println name
// }
    def varMap = [:]
varMap["name"] = [] 

def binding = new Binding(varMap)
def shell = new GroovyShell(binding)

def function2 = { name ->
    name.each { println "test item: ${it}" }
}

// ------ main

// load Config and evaluate it
def configText = new File(args[0]).getText()
shell.evaluate(configText)

def name = varMap["name"] 


function2(name)
    }
