node {
 stage "checkout"
 git url: 'https://github.com/mirumee/saleor.git'
 sh """ 
    whoami
    id
    sudo docker-compose  build
    sudo docker-compose run web python manage.py migrate
    sudo docker-compose run web python manage.py populatedb --createsuperuser
    sudo docker-compose -d up
    """
} 
