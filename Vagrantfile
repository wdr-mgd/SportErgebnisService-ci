

Vagrant.configure(2) do |config|

  access_key_id = ENV['AWS_ACCESS_ID']
  secret_access_key = ENV['AWS_SECRET_ACCESS_KEY']

  config.vm.box = "dummy"
  config.vm.synced_folder "vagrant/", "/vagrant"

  config.vm.provider :aws do |aws, override|
    aws.access_key_id = access_key_id
    aws.secret_access_key = secret_access_key
    aws.keypair_name = "aws-docker-box"
    aws.instance_type = "t2.small"
    aws.region = "eu-central-1"
    aws.security_groups = ["ssh", "GoCD"]
    aws.elastic_ip = "52.28.171.249"

    aws.ami = "ami-858065ea"

    override.ssh.username = 'ubuntu'
    override.ssh.private_key_path = "./aws-docker-box.pem"
  end

  config.vm.provision "fix-no-tty", type: "shell" do |s|
      s.privileged = false
      s.inline = "sudo sed -i '/tty/!s/mesg n/tty -s \\&\\& mesg n/' /root/.profile"
  end

  config.vm.provision :shell, :inline => "sudo cp /vagrant/cruise-config.xml /etc/go/"
  config.vm.provision :shell, :inline => "sudo cp /vagrant/passwd /etc/go/"
end
