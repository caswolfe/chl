# Commands & Documentation

[Ubuntu](#Ubuntu)  
[Anaconda](#Anaconda)  
[Docker](#Docker)  

## Ubuntu

#### updating ubuntu
`sudo apt update`  
`sudo apt upgrade`  

#### restarting ubuntu  
`sudo shutdown -r now`  

#### shutting down ubuntu
`sudo shutdown now`

## Anaconda
[Anaconda Docs](https://docs.conda.io/projects/conda/en/latest/index.html)

#### create environment
`conda env create -f environment.yml`

#### activate environment
`conda activate environment`

#### deactivate environment
`conda deactivate environment`

#### list environments
`conda env list`

#### remove environment
`conda env remove --name environment`

#### update environment
`conda env update --file environment.yml --prune`

## Docker  
[Docker Docs](https://docs.docker.com/engine/reference/commandline/docker/) 

### Container: chl_mysql
1) create docker container 
   1) `docker run -d --name chl_mysql -v ~/chl_mysql:/var/lib/mysql --network host -p 3306:3306 -e TZ=UTC -e MYSQL_ROOT_PASSWORD=password ubuntu/mysql`
2) login as the root user
   1) `docker exec -it chl_mysql mysql -uroot -p`
3) create a new "robot" user, then exit
   1) `create user 'robot'@'%' identified by 'password';`
      1) *don't forget to change the password from "password" itself*
   2) `grant all privileges on *.* to 'robot'@'%' with grant option;`
   3) `flush privileges;`
   4) `exit`
4) restart the docker container
   1) `docker restart chl_mysql`

### Container: chl_grafana
1) create docker container
   1) `docker run -d --name chl_grafana --network host -p 3000:3000 grafana/grafana-oss`
