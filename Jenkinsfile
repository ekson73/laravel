node('php'){
    stage('Initial Clean'){
        deleteDir()
        sh 'ls -la'
    }

    stage('Fetch') {
        checkout scm
    }

    stage('Build for Tests'){
        sh 'composer install --no-scripts --prefer-dist --ignore-platform-reqs'
    }

    stage('config') {
        parallel(
            'Copy .env file': {
                echo 'cp .env.example .env'
            },
            'config route': {
                echo 'Tarefa Paralela 02'
            }
        )
    }

    //stage('Tests') {
    //    sh 'php ./vendor/bin/phpunit'
    //}

    stage('Build'){
        sh 'composer install --no-scripts --prefer-dist --no-dev --ignore-platform-reqs'
    }

    stage('Docker Build') {
        sh 'docker build -t ekson73/laravel:$BUILD_NUMBER .'
    }

    stage('Docker Ship') {
        sh 'docker push ekson73/laravel:$BUILD_NUMBER'
    }
    
    stage('Final Clean'){
        // deleteDir()
        sh 'ls -la'
    }
}
