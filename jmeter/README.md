#Install Java

Centor/Rocky Linux

dnf install -y java-17-openjdk java-17-openjdk-devel

Ubuntu

sudo apt update

sudo apt install -y openjdk-17-jdk

java -version

#Download jmeter

wget https://downloads.apache.org/jmeter/binaries/apache-jmeter-5.6.3.tgz


#extract dan pindahkan

tar -xvzf apache-jmeter-5.6.3.tgz

sudo mv apache-jmeter-5.6.3 /opt/jmeter

echo 'export JMETER_HOME=/opt/jmeter' | sudo tee -a /etc/profile

echo 'export PATH=$JMETER_HOME/bin:$PATH' | sudo tee -a /etc/profile

source /etc/profile

#Test

jmeter -n -t /path/to/test_plan.jmx -l /path/to/result.jtl -e -o /path/to/report/
