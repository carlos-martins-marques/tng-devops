# tng-devops
<p align="center"><img src="https://github.com/sonata-nfv/tng-devops/wiki/images/sonata-5gtango-logo-500px.png" /></p>

This repository is used to handle the multiple environments for 5GTANGO and the deployment of the SDK, Service Platform and the VnV. The strategy of deployment is developed in Ansible. The playbooks will be executed by Jenkins.

## Organization of the repository
* environments: This file contains the list of IP servers to deploy the platforms grouped by 5GTANGO environments
* host_vars: This folder contains a file per server with the specific variables to deploy the platform
* utils: This folder contains some utilities to handle the servers
* roles: Being a Ansible role based structure we have a folder (roles) with roles to deploy each platform (sdk, sp and vnv). Inside the roles folder we have the tasks that contains the playbooks to deploy each platform component.

This is the tree structure of the repository:
```
.
├── environments
├── host_vars
│   ├── int-sp-ath.5gtango.eu
│   ├── int-vnv-bcn.5gtango.eu
│   ├── pre-int-sdk-ath.5gtango.eu
│   ├── pre-int-sp-ath.5gtango.eu
│   ├── pre-int-vnv-bcn.5gtango.eu
│   ├── qual-sp-bcn.5gtango.eu
│   ├── qual-vnv-bcn.5gtango.eu
│   ├── sta-sdk-ath.5gtango.eu
│   ├── sta-sdk-ave.5gtango.eu
│   ├── sta-sdk-pad.5gtango.eu
│   ├── sta-sp-ath.5gtango.eu
│   ├── sta-sp-ave.5gtango.eu
│   ├── sta-sp-pad.5gtango.eu
│   ├── sta-vnv-ath.5gtango.eu
│   ├── sta-vnv-ave.5gtango.eu
│   ├── sta-vnv-pad.5gtango.eu
│   └── localhost
├── roles
│   ├── sp
│   │   └── tasks
│   │       ├── main.yml
│   │       └── components.yml
│   ├── sdk
│   │   └── tasks
│   │       ├── components.yml
│   │       └── main.yml
│   ├── vnv
│   │   └── tasks
│   │       ├── components.yml
│   │       └── main.yml
│   ├── sp.yml
│   ├── sdk.yml
│   └── vnv.yml
├── LICENSE
├── README.md
└── utils
    ├── destroy.yml
    └── install-pip.yml
```

## Developing
### Built with
This scripts are built with ansible > 2.4

### Prerequisites
* ansible > 2.4
* docker > 17.12.0-ce
* docker-py = 1.9.0

## Setting up Dev
Here's a brief intro about what a developer must do in order to start developing the project further:
```
git clone https://github.com/sonata-nfv/tng-devops.git
cd tng-devops/
```

## Usage
Here is the list of commands to deploy each environment

* int-sp-ath.5gtango.eu

`ansible-playbook roles/sp.yml -i environments -e "target=int-sp"`

* int-vnv-bcn.5gtango.eu

`ansible-playbook roles/vnv.yml -i environments -e "target=int-vnv"`

* pre-int-sdk-ath.5gtango.eu

`ansible-playbook roles/sdk.yml -i environments -e "target=pre-int-sdk"`

* pre-int-sp-ath.5gtango.eu

`ansible-playbook roles/sp.yml -i environments -e "target=pre-int-sp"`

* pre-int-vnv-bcn.5gtango.eu

`ansible-playbook roles/vnv.yml -i environments -e "target=pre-int-vnv"`

* qual-sp-bcn.5gtango.eu

`ansible-playbook roles/sp.yml -i environments -e "target=qual-sp"`

* qual-vnv-bcn.5gtango.eu

`ansible-playbook roles/vnv.yml -i environments -e "target=qual-vnv"`

* sta-sdk-ath.5gtango.eu, sta-sdk-ave.5gtango.eu and sta-sdk-pad.5gtango.eu

`ansible-playbook roles/sdk.yml -i environments -e "target=sta-sdk"`

* sta-sp-ath.5gtango.eu, sta-sp-ave.5gtango.eu and sta-sp-pad.5gtango.eu

`ansible-playbook roles/sp.yml -i environments -e "target=sta-sp"`

* sta-vnv-ath.5gtango.eu, sta-vnv-ave.5gtango.eu and sta-vnv-pad.5gtango.eu

`ansible-playbook roles/vnv.yml -i environments -e "target=sta-vnv"`

Or it can be deployed directly deployed using the hostname of the environment like:

`ansible-playbook roles/sp.yml -i environments -e "target=sta-sp-ath.5gtango.eu"`

## Contributing
To contribute to the development of the tango devops you have to fork the repository, commit new code and create pull requests.

## Licensing
This repository is under Apache 2.0 License

## Lead Developers
@fjvicens Felipe Vicens 
@arocha7 Alberto Arocha