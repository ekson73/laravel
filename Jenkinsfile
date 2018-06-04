node('php'){
    stage('Clean'){
        deleteDir()
        sh 'ls -la'
    }

    stage('Fetch') {
        checkout scm
    }

    stage('Docker Build') {
        sh 'docker build -t ekson73/laravel:$BUILD_NUMBER .'
    }

    stage('Docker Ship') {
        sh 'docker push ekson73/laravel:$BUILD_NUMBER'
    }
    
    stage('Docker Clean') {
        sh 'docker rmi -f ekson73/laravel:$BUILD_NUMBER'
    }
}
