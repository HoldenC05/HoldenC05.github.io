**Install Docker**
- install docker
	- sudo apt install docker.io
- Install Docker Composer
	`sudo apt install docker-compose`

**Install WordPress (Using a Git Repo)**
- Clone repo to build .yml file (so i didn't have to copy and paste it)
	- `sudo git clone https://github.com/Alujjdnd/DockerWordpress.git`
- Install other neccessary packages just in case
	- `sudo apt-get install libffi-dev libssl-dev 
	- `sudo apt install python3-dev`
	- `sudo apt-get install -y python3 python3-pip`

**Fixing Errors**
- Try and build the docker container
	- `docker-compose up`
	- Would not build  - "Permission Denied"
		- `sudo usermod -aG docker $USER`
		- `sudo systemctl restart docker`

**Worked!!**
- Build the container
	- `sudo docker-compose up`

**Access gui using web**
- go to localhost/ on web
- Follow gui steps to define username and password etc.

![](Picture/Screenshot 2024-11-03 at 4.48.34 PM.png?raw=true "1")

![](Picture/Screenshot 2024-11-03 at 4.49.23 PM.png?raw=true "2")

![](Picture/Screenshot 2024-11-03 at 4.52.33 PM.png?raw=true "3")

![](Picture/Screenshot 2024-11-03 at 4.52.55 PM.png?raw=true "4")