pipeline {
    agent any

    environment {
        DOCKERHUB_CREDENTIALS = credentials('docker') // Jenkins에 등록한 Docker Hub 자격 증명
        IMAGE_NAME = "luckyjakey/nginx" // Docker Hub 이미지 이름
        TAG = "latest" // 이미지 태그 (원하는 태그로 변경)
    }

    stages {
        stage('Checkout') {
            steps {
                // 소스 코드 체크아웃 (예: Git, SVN 등)
                checkout scm
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    // Docker 이미지 빌드
                    def dockerImage = docker.build("luckyjakey/nginx:v1", "--file Dockerfile .")

                    // Docker Hub에 로그인
                    docker.withRegistry('https://index.docker.io/v2/', 'dckr_pat_Lt0bzfliwYJj6FnY-2-goug2e9E
') {
                        // Docker 이미지 푸시
                        dockerImage.push()
                    }
                }
            }
        }
    }
}
