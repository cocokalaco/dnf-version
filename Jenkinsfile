pipeline {
    agent any

    parameters {
        string(name: 'BRANCH', defaultValue: 'main', description: '代码分支')
        string(name: 'DNF_VERSION_FOLDER', defaultValue: '70', description: '输入部署版本')
    }

    stages {

        stage('替换版本') {
            steps {
                script {
                    sh '''
                    echo "获取目标版本: $DNF_VERSION_FOLDER"
                    '''
                }
            }
        }

//         stage('滚动更新') {
//             agent {
//                 docker {
//                     image 'bitnami/kubectl:latest' // 使用 Bitnami 提供的 kubectl 容器
//                     args '--entrypoint=' // 防止镜像报错
//                 }
//             }
//             environment {
//                 K8S_API_SERVER = "https://172.31.0.7:6443" // 替换为你的 API Server 地址
//                 K8S_SA_TOKEN = credentials('k8s_token')  // 获取 ServiceAccount Token
//             }
//             steps {
//                 sh '''
//                     echo "当前部署namespace为: $KUBE_NAMESPACE, 版本号为: $BUILD_NUMBER"
//
//                     echo "强制滚动更新"
//                     kubectl --server=$K8S_API_SERVER \
//                             --token=$K8S_SA_TOKEN \
//                             --insecure-skip-tls-verify \
//                             rollout restart deployment/dnf-server-new -n dnf-server
//                 '''
//             }
//         }
    }

    post {
        cleanup {
            cleanWs()
            echo 'this is the overall post cleanup message'
        }
    }
}
