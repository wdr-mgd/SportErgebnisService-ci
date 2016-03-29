# Initial setup

### Vagrant and AWS Plugin

1. If you haven't already, [install *Vagrant*](https://www.vagrantup.com/docs/installation/)

- Install the *vagrant-aws plugin*
```
vagrant plugin install vagrant-aws
vagrant box add dummy https://github.com/mitchellh/vagrant-aws/raw/master/dummy.box
```

### SSH Keys and AWS Credentials

1. Retrieve the keypair file `aws-docker-box.pem` from *Files -> AWS Keypair File* in the `keys.kdb` file (using KeePassX v0.4.x, please get the password from the project team) and store it in this repository's root folder.

2. Retrieve the AWS credentials from *Keys -> AWS ID and SECRET* in the `keys.kdb` file and export it in the shell
```
export AWS_ACCESS_ID=[Username in keys.kdb]
export AWS_SECRET_ACCESS_KEY=[Password in keys.kdb]
```
To ssh onto the AWS Go-Box run: ssh -i [path to aws docker box pem file] ubuntu@ec2-52-28-171-249.eu-central-1.compute.amazonaws.com

# Starting the VM on AWS (make sure it's not running yet)
```
vagrant up
```
This will start a EC2 Container Services VM with two Docker containers:   
1. gocd-server
2. gocd-agent1

Open http://52.28.171.249:8153/ in your browser to access the Go CD server.

