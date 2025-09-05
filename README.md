db서버용

ubuntu
sudo passwd
1234
sudo apt update && sudo apt upgrade -y
date
sudo apt install -y tzdata
sudo apt install mysql-server
sudo systemctl start mysql
sudo systemctl enable mysql
sudo vim /etc/mysql/mysql.conf.d/mysqld.cnf
sudo /etc/init.d/mysql restart


spring 용

> ubuntu
> sudo passwd
> 1234
> sudo apt update && sudo apt upgrade -y
> sudo apt install -y tzdata
> sudo dpkg-reconfigure tzdata
> sudo date
> export TZ=Asia/Seoul
> sudo apt-get install openjdk-17-jdk (창 나오면 엔터 혹은 →, 엔터)
> vim ~/.bashrc

최하단에 추가

export JAVA_HOME=$(dirname $(dirname $(readlink -f $(which java))))
export PATH=$PATH:$JAVA_HOME/bin

> source ~/.bashrc
> echo $JAVA_HOME

> sudo fallocate -l 2G /swapfile
sudo chmod 600 /swapfile
> sudo mkswap /swapfile
> sudo swapon /swapfile
> echo '/swapfile none swap sw 0 0' | sudo tee -a /etc/fstab
> free -h

> git clone
> chmod +x ./gradlew
> ./gradlew build
> java -jar build/libs/app.jar

> sudo apt install iptables-persistent
> sudo iptables -t nat -A PREROUTING -p tcp --dport 80 -j REDIRECT --to-ports 10000
> sudo chmod 777 /etc/iptables/rules.v4
> sudo iptables-save > /etc/iptables/rules.v4
> cat /etc/iptables/rules.v4

spring 용 해설

ubuntu
sudo passwd
1234
su root / su ubuntu
	// 사용자 변경
sudo apt update && sudo apt upgrade -y
date
sudo apt install -y tzdata
sudo dpkg-reconfigure tzdata
export TZ=Asia/Seoul
	// 한국 시간으로 설정
sudo apt install openjdk-17-jdk
vim ~/.bashrc
	// 환경변수 설정
	// 맨 밑으로 가서 (대문자 G)
export JAVA_HOME=$(dirname $(dirname $(readlink -f $(which java))))
export PATH=$PATH:$JAVA_HOME/bin
	// 복붙 후 esc 누르고 :wq
source ~/.bashrc
	// 변경한 설정 반영
java -version
javac -version
	// 자바 버전 확인
sudo apt install mysql-server
sudo systemctl start mysql
sudo systemctl enable mysql
sudo vim /etc/mysql/mysql.conf.d/mysqld.cnf
sudo /etc/init.d/mysql restart
