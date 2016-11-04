node {
 stage "checkout"
 git url: 'https://github.com/mirumee/saleor.git'
 sh """ 
    sudo docker-compose --project-name=${JOB_NAME} stop
    sudo docker-compose --project-name=${JOB_NAME} rm --force
    sudo docker stop `docker ps -a -q -f status=exited`
    sudo docker rm -v `docker ps -a -q -f status=exited`
    sudo docker rmi `docker images --filter 'dangling=true' -q --no-trunc` || /bin/true
    sudo docker-compose --project-name=${JOB_NAME} build
    sudo docker-compose run web python manage.py migrate
    sudo docker-compose run web python manage.py populatedb --createsuperuser
    sudo docker-compose -d up
    """
} 
