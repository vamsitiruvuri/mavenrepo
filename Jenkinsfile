pipeline{
agent { label 'dev' }
stages{
stage('1'){
steps{
checkout([$class: 'GitSCM', 
    branches: [[name: '*/master']], 
    userRemoteConfigs: [[credentialsId: '622ab12e-e476-4699-8438-42a5ae5932e9', url: 'https://github.com/vamsitiruvuri/mavenrepo.git']]
])

}
}

stage('build'){
steps{
sh 'mvn package'

}
}

stage('sonar'){
steps{
withSonarQubeEnv('sonar'){
sh "mvn sonar:sonar"
}


}
}

stage('tomcat'){
steps{
sh 'scp /root/workspace/samplejob/target/studentapp-2.5-SNAPSHOT.war 52.66.239.226:/var/lib/tomcat/webapps'

}
}


}
}
