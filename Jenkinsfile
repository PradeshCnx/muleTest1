pipeline{
	agent any	
	stages{
		stage('Build'){
			steps{
				git branch: 'devlop', credentialsId: 'cabbdcc2-ae95-42d9-a016-50786bff5726', url: 'https://github.com/PradeshCnx/muleTest1.git'
				bat "mvn -Dmaven.test.failure.ignore-true clean package"
			}
		}
		stage('Munit Testing'){
			steps{
				git branch: 'devlop', credentialsId: 'cabbdcc2-ae95-42d9-a016-50786bff5726', url: 'https://github.com/PradeshCnx/muleTest1.git'
				bat "mvn -Dmaven.test.failure.ignore=true clean test"
				publishHTML([allowMissing: false, alwaysLinkToLastBuild: false, keepAll: false, reportDir: 'target\\munit-reports\\coverage', reportFiles: 'summary.html', reportName: 'Code Coverage', reportTitles: ''])
			}
		}
		stage('Deploy'){
			steps{
				git branch: 'devlop', credentialsId: 'cabbdcc2-ae95-42d9-a016-50786bff5726', url: 'https://github.com/PradeshCnx/muleTest1.git'
				bat "mvn -Dmaven.test.failure.ignore-true clean deploy -DmuleDeploy -DskipTests -Dmule.version=4.4.0 -Danypoint.username=PradeshTrix -Danypoint.password=Mulesoft-123 -Denv=Sandbox -Dappname=muletest1 -Dbusiness=concentrix -DvCore=Micro -Dworkers=1 -DaltDeploymentRepository=myinternalrepo::default::file:///C:/muleRepo"
			}
		}
	}

}
