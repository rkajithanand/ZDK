#!groovy

{
    def toolbelt = tool 'toolbelt'

    // -------------------------------------------------------------------------
    // Check out code from source control.
    // -------------------------------------------------------------------------

    // stage('checkout source') {
    //     checkout scm
    // }


    // -------------------------------------------------------------------------
    // Run all the enclosed stages with access to the Salesforce
    // JWT key credentials.
    // -------------------------------------------------------------------------

 	withEnv(["HOME=${env.WORKSPACE}"]) {	

		// stage('Authorize to ZDK') {
		// 	rc = command "${toolbelt}/zdk auth:login"
		//     if (rc != 0) {
		// 	error 'Salesforce org authorization failed.'
		//     }
		// }

		stage('Deploy and Run Tests') {
			def command = "${toolbelt}/zdk org:push"  // Replace with your command
			def process = command.execute()  // Execute the command
			def output = process.text  // Capture the output as a string
			
			println "Output:\n$output"  // Print the command output
		}

		// stage('Validate the results') {
		//         for(int i = 0 ; i < 10 ; i++)
		//         {
		//   		    rc = command "${toolbelt}/zdk org:push"
		//   		    if (rc != 0) {
		//   			error 'Salesforce deploy and test run failed.'
		//   		    }
		//         }
		// }
  }
}

def command(script) {
    if (isUnix()) {
        return sh(returnStatus: true, script: script);
    } else {
		return bat(returnStatus: true, script: script);
    }
}
