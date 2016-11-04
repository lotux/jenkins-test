node {
 stage "checkout"
 git url: 'https://github.com/mirumee/saleor.git'
 env.DOCKER_HOST = "-H unix:///var/run/docker.sock --tls=false"
 sh """ 
    docker-compose build
    docker-compose run web python manage.py migrate
    docker-compose run web python manage.py populatedb --createsuperuser
    docker-compose up
    """
} 
