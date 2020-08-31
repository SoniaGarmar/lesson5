node('master') { //branch where we want to execute our pipe line
    //we have defines several stages tetch source code, testing, and deployment
    stage("Fetch Source Code") { //get the code
       cleanWs() //clean workspace before start building
        git ([url:'https://github.com/SoniaGarmar/lesson5', branch:'add-functions-and-test'])
    }
    
    dir('.') {//once we have the code, we move to the current directory where we want to execute the unit tests for functions.py
        printMessage('Running Pipeline')
        stage("Testing") { //in this stage we run the tests in the test_function file
            sh 'ls -la' //make sure python is installed
            sh 'apk add python'
            sh 'python test_functions.py'
        }
        stage("Deployment") {//in this stage we chek if the branch name is master an print one mesage or another
            if (env.BRANCH_NAME == 'master') {
                printMessage('Deploying the master branch')
            } else {
                printMessage("No deployment for branch [${env.BRANCH_NAME}]")
            }
            
        }
        printMessage('Pipeline Complete')
    }
}

def printMessage(message) {
    echo "${message}"
}