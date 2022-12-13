# ktds-MSP-ansible
IT 인프라 자동화 테스트용 ansible 소스

 - Playbook 실행 방법(사전에 hosts에 host 정의 필수)
```shell
 # ansible-playbook -l {HOST_IP or HOST_GROUP_NAME} {PLAYBOOK_NAME} 
 $ ansible-playbook -l DB playbook/db/start_mysqld.yml # HOST_IP 
 $ ansible-playbook -l 10.0.1.167 playbook/db/start_mysqld.yml # HOST_GROUP_NAME
```
