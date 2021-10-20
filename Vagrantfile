$mysql = <<-SCRIPT
  apt-get update && \
  apt-get install -y mysql-server-5.7 && \
  cat /vagrant/mysql/mysqld.cnf > /etc/mysql/mysql.conf.d/mysqld.cnf && \
  service mysql restart
SCRIPT

Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/bionic64"


  config.vm.define "msqlserver" do |mysql|
    mysql.vm.network :forwarded_port, guest: 3306, host: 3306
    
    mysql.vm.provision :shell, inline: $mysql
  end
end
