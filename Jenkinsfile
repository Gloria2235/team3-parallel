pipeline{
	agent {
		label {
		 label 'slave1'
		}
	} 
	stages{
		stage('git-clone'){
			steps{
				checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: 'github-id', url: 'https://github.com/Gloria2235/team3-parallel.git']]])
			}
		}
		stage('parallel-level'){
			parallel {
				stage('sub-job1'){
					steps{
						echo "sub-job1 task"
					}
				}
				stage('sub-job2'){
					steps{
						echo "sub-job2 task"
					}
				}
				stage('user-check'){
					steps{
						sh  'cat /etc/passwd'
					}
				}
			}
		}
		stage('version-check'){
			agent {
			 label {
			  label 'slave2'
			 }
			}
			steps{
				echo "end of parallel jobs"
			}
		}
		stage('web-fix'){
			steps{
				echo "webhook fix"
			}
		}
	}
}
