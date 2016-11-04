node {
 stage "checkout"
 git url: 'https://github.com/mirumee/saleor.git'
 sh """ 
    whoami
    id
    docker-compose build
    docker-compose run web python manage.py migrate
    docker-compose run web python manage.py populatedb --createsuperuser
    docker-compose up
    """
} 
