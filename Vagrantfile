

Vagrant.configure(2) do |config|

  access_key_id = ENV['AWS_ACCESS_ID']
  secret_access_key = ENV['AWS_SECRET_ACCESS_KEY']

  config.vm.box = "dummy"

  config.vm.provider :aws do |aws, override|
    aws.access_key_id = access_key_id
    aws.secret_access_key = secret_access_key
    aws.keypair_name = "aws-docker-box"
    aws.instance_type = "t2.small"
    aws.region = "eu-central-1"
    aws.security_groups = ["ssh", "GoCD"]

    aws.ami = "ami-7ce3f910"

    override.ssh.username = 'ec2-user'
    override.ssh.private_key_path = "./aws-docker-box.pem"
  end

  config.vm.provision :shell, :inline => "docker restart gocd-server"
  config.vm.provision :shell, :inline => "docker restart gocd-agent1"
end
