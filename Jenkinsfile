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
				expression{ 
					params.action == 'apply'
				}
			}
			steps{
				echo "initilization completed..."
			}
		}
		stage("terraform fmt"){
			when {
				expression{ 
					params.action == 'apply'
				}
			}
			steps{
				echo "fmt completed..."
			}
		}
		stage("terraform validation"){
			when {
				expression{ 
					params.action == 'apply'
				}
			}
			steps{
				echo "validation completed..."
			}
		}
		stage("terraform plan"){
			when {
				expression{ 
					params.action == 'apply'
				}
			}
			steps{
				echo "plan completed..."
			}
		}
		stage("terraform apply"){
			when {
				expression{ 
					params.action == 'apply'
				}
			}
			
			steps{
				input{
				    message "Should we Continue"
				    ok "Yes, we should."
  			}
				echo "apply completed..."
			}
		}
		stage("terraform destroy"){
			when {
				expression{ 
					params.action == 'destroy'
				}
			}
			
			steps{
				input{
				    message "Should we Continue"
				    ok "Yes, we should."
  				}
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