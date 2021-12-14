## 서버 관련 정보 확인(포트 정보 등)

netstat -a
netstat -tnl 포트 확인
cd tail -f catalina.out

netstat -tnlp | grep -v 127.0.0.1 | sed 's/:::/0 /g' | sed 's/[:\/]/ /g' | awk '{print$5"\t"$10} | sort -ug

특정 port 만 확인하고 싶을 경우 

netstat -tulpn | grep 포트번호

를 사용하면 된다. 

## 방화벽 특정 포트 설정 명령

CentOS 7 firewall-cmd--permanent--zone=public--add-port=1234/tcp
CentOS 7 firewall-cmd--permanent--zone=public--remove-port=1234/tcp

CentOS 6 iptables -I INPUT 1 -p tcp --dport 1234 -j ACCEPT
CentOS 6 iptables -D INPUT -p tcp --dport 1234 -j ACCEPT

firewall-cmd --list-all
iptables -L -v

