# Initial setup

If you haven't already, [install *Vagrant*](https://www.vagrantup.com/docs/installation/)

Install the *vagrant-aws plugin*
```
vagrant plugin install vagrant-aws
```

Retrieve the keypair file `aws-docker-box.pem` from *Files -> AWS Keypair File* in the `keys.kdb` file (using KeePassX v0.4.x, please get the password from the project team) and store it in this repository's root folder.

Retrieve the AWS credentials from *Keys -> AWS ID and SECRET* in the `keys.kdb` file and export it in the shell
```
export AWS_SECRET_ACCESS_KEY=[Username in keys.kdb]
export AWS_ACCESS_ID=[]
```