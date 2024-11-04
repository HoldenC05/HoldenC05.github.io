**Install Docker**
- Install Docker
	-`sudo apt install docker.io`
- Install Docker Compose
	`sudo apt install docker-compose`

**Install WordPress (Using a Git Repo)**
- Clone the repository to obtain the .yml file without the need for manual copying and pasting
	- `sudo git clone https://github.com/Alujjdnd/DockerWordpress.git`
- Install Other Necessary Packages Just in Case
	- `sudo apt-get install libffi-dev libssl-dev`
	- `sudo apt install python3-dev`
	- `sudo apt-get install -y python3 python3-pip`

**Fixing Errors**
- Try and Build the Docker Container
	- `docker-compose up`
	- "Would not build - Permission Denied"
		- `sudo usermod -aG docker $USER`
		- `sudo systemctl restart docker`

**Worked!!**
- Build the Container
	- `sudo docker-compose up`

**Access GUI using web**
- Go to localhost/ on web
- Follow GUI steps to define username and password etc.

![Screenshot of Docker installation step 1](Picture/Screenshot 2024-11-03 at 4.48.34 PM.png?raw=true "1")

![WordPress setup step 2](Picture/Screenshot 2024-11-03 at 4.49.23 PM.png?raw=true "2")

![Screenshot of Docker installation step 3](Picture/Screenshot 2024-11-03 at 4.52.33 PM.png?raw=true "3")

![WordPress setup final step](Picture/Screenshot 2024-11-03 at 4.52.55 PM.png?raw=true "4")