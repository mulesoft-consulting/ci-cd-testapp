pipeline{
 agent any
 environment {
    ANYPOINT = credentials('ANYPOINT')
 }
 stages {
 	stage ('Build'){
 		steps {
 			withMaven(maven:'maven'){
 				sh 'mvn -f pom.xml clean install'
 			}
 		}
 	}
 	stage ('Deploy'){
 		steps {
 			withMaven(maven:'maven'){
 				sh 'mvn -f pom.xml package deploy  -Dusername=$ANYPOINT_USR -Dpassword=$ANYPOINT_PSW -Denvironment=Sandbox -DmuleDeploy'
 			}
 		}
 	}
 }
}