pipeline{
	agent{
		label 'agent'
	}
	options{
	  timeout(time: 30, unit: 'MINUTES')
	  disableConcurrentBuilds()
	  ansiColor('xterm')
	}
	parameters { 
		choice(name: 'action', choices: ['apply', 'destroy'], description: 'Enter your actions') 
	}
	stages{
		stage("checkout"){
			steps{
				echo "git clone sucessfully"
			}
		}

		stage("terraform init"){
			when {
				action == 'apply'
			}
			steps{
				echo "initilization completed..."
			}
		}
		stage("terraform fmt"){
			when {
				action == 'apply'
			}
			steps{
				echo "fmt completed..."
			}
		}
		stage("terraform validation"){
			when {
				action == 'apply'
			}
			steps{
				echo "validation completed..."
			}
		}
		stage("terraform plan"){
			when {
				action == 'apply'
			}
			steps{
				echo "plan completed..."
			}
		}
		stage("terraform apply"){
			when {
				action == 'apply'
			}
			input{
			    message "Should we Continue"
			    ok "Yes, we should."
  			}
			steps{
				echo "apply completed..."
			}
		}
		stage("terraform destroy"){
			when {
				action == 'destroy'
			}
			input{
			    message "Should we Continue"
			    ok "Yes, we should."
  			}
			steps{
				echo "apply completed..."
			}
		}
	}
	post{
  		always{
    		deleteDir()
  		}
    }
}