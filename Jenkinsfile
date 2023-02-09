pipeline {
    agent any

    stages {
        stage('Hello') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/master']],
                doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [],
                userRemoteConfigs: [[credentialsId: '2f23d7ee-b4a1-4e76-9060-1d31000f616a', url:
                'https://gh.api.99988866.xyz/https://github.com/copy-black/web-demo4.git']]])
            }
        }
        stage('编译构建') {
            steps {
                bat label: '', script: 'mvn clean package'
            }
        }
        stage('项目部署') {
            steps {
            deploy adapters: [tomcat8(credentialsId: 'b2438dcf-a755-4208-a72e-a528fd6bea47', path: '', url: 'http://127.0.0.1:8881')], contextPath: null,
            war: 'target/*.war'
            }
        }
    }
}
