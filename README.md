
<!-- PROJECT LOGO -->
<br />
<p align="center">
 

  <h3 align="center">Jenkins CI/CD project </h3>

  <p align="center">
    An awesome task which allowed me to understand atomated CI/CD Github integration project
    <br />
    <br />

  </p>
</p>



<!-- TABLE OF CONTENTS -->
## Table of Contents

* [About the Project](#about-the-project)
* [Getting Started](#getting-started)
  * [Prerequisites](#prerequisites)
  * [Installation](#installation)
  
* [Usage](#usage)
* [Contributing](#contributing)
* [License](#license)
* [Contact](#contact)



<!-- ABOUT THE PROJECT -->
## About The Project

Automated CI/CD pipeline for Nodejs application. 

Here's important point of this assignment:

* Integrate GitHub with Jenkins Tools code automatically triggered
from GitHub.
* Automated CI/CD pipeline for NodeJS application using AWS EC2, Docker, Github and Jenkins.
* Implemented Github web hook Integration for deploying docker application on EC2 instances using declarative pipeline


<!-- GETTING STARTED -->
## Getting Started

To get a local copy up and running follow these simple example steps.

### Prerequisites

* AWS EC2 instance
* Jenkins
* Docker
* Docker-compose
* GitHub 
* Github integration plugin installed in jenkins

### Installation:

Follow this link for installation of Docker and Jenkins
https://medium.com/@sanjuthamke9699/day-7-task-understanding-package-manager-and-systemctl-fc481197c564

Follow thsi link for installation of Docker compose 
https://medium.com/@sanjuthamke9699/day-18-task-docker-compose-project-for-devops-engineers-af5d4c6c48c5



### Steps :

1. Launch EC2 instance
2. Install Jenkins,Docker,docker-compose
3. Fork the reposotory https://github.com/sanjanathamke/Jenkinproject.git
4. Clone the repo on EC2 
```sh
git clone https://github.com/sanjanathamke/Jenkinproject.git
```


3. create SSH public and private key
```sh
ssh-keygen
cd .ssh
ls
cat id_rsa
cat id_rsa.pub
```

4.Configuring GitHub

* Click to Github Account Settings 
* Click on SSH and GPG keys
* Enter public ip of EC2 instance
* Click on Add SSH key


5. Configuring GitHub-Webhook

* Go to your GitHub repository and click on Settings
* Click on Webhooks and then click on Add webhook
* In the ‘Payload URL’ field, paste your Jenkins environment URL.At the   end of this URL add /github-webhook/. In the ‘Content type’ select: ‘application/json’ and leave the ‘Secret’ field empty.
* Click on Add Webhook

6. Open Jenkins on publicIp:8080 on browser

7. Installing GitHub integration plugin 
* Click on Manage Jenkins on left panel
* Manage plugin 
* Available plugin
* github integration 
* install it


8. Steps of Jenkins CI/CD pipeline

1. Add freestyle project
* Enter item name and select freestyle project options 
* Click on Ok
2. Project configuration
* Enter description 
* Select checkbox Github project 
* Enter github url of project
3. In Source Code Management 
* Select Git 
* Enter github url 
* In credentials click on Add
4. Add credentials
* Select kind as SSH username with private key 
* Enter ID 
* Enter Description 
*  Enter Username as instance username 
* In private key Enter private key of instance
* click on add
5. In Build trigger select Github hook trigger for GITScm polling 
6. Build steps 
* Select Execute shell 
* Enter commands of docker compose and save the configuration
```sh
echo "starting container"
docker-compose down
docker-compose up -d --no-deps --build <service_name>

```

[Note : To rebuild the image before starting the container. It is not sufficient to simply start and stop the old container; it must rebuild the image and then only copy new files into the container.

```sh
$ docker-compose up -d --no-deps --build <service_name>
```

--no-deps - Don't start linked services.
--build - Build images before starting containers.
]

* Check the web-hook connection of Github project , it should have a green checkmark.

* Go to dashboard then go to project page by clicking on project name
* Click on build now and see status on left panel
* Click on status of project under build history and then click on console output
* Access the url public_ip of instance: 8000 on browser
* Now make changes in code and push to Github main branch ,and refresh page so you will see changes
* Access the url again


<!-- USAGE EXAMPLES -->
## Usage

_For more examples, please refer to the [Documentation](Link to Refer a project: 

https://medium.com/@sanjuthamke9699/day-24-task-complete-jenkins-ci-cd-project-158c10fdf55d )


<!-- CONTRIBUTING -->
## Contributing

Contributions are what make the open source community such an amazing place to be learn, inspire, and create. Any contributions you make are **greatly appreciated**.

1. Fork the Project
2. Create your Feature Branch (`git checkout -b feature/AmazingFeature`)
3. Commit your Changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the Branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request



<!-- LICENSE -->
## License

Distributed under the MIT License. See `LICENSE` for more information.



<!-- CONTACT -->
## Contact

Sanjana Thamke - www.linkedin.com/in/sanjana-thamke-68827417b - My LinkedIn

Project Link: https://github.com/sanjanathamke/Jenkinproject.git




