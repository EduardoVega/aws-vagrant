Vagrant.configure("2") do |config|
    config.vm.box = "dummy.box"

    config.vm.synced_folder ".", "/vagrant", disabled: true
  
    config.vm.provider :aws do |aws, override|
      aws.access_key_id = ENV['ACCESS_KEY']
      aws.secret_access_key = ENV['SECRET_KEY']
      aws.keypair_name = ENV['PRIVATE_KEY_NAME']
      aws.ami = ENV['AMI_ID']
      aws.region = "us-east-1"
      aws.instance_type = "t2.micro"
      aws.security_groups = ENV['SECURITY_GROUP']
      aws.associate_public_ip = true
      aws.subnet_id = ENV['SUBNET_ID']
      aws.tags = {
        'Name' => ENV['INSTANCE_NAME'],
        'Type' => 'Vagrant',
      }
      override.ssh.username = "centos"
      override.ssh.private_key_path = ENV['PRIVATE_KEY']

    end
end