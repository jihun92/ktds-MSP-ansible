# ktds-MSP-ansible
IT 인프라 자동화 테스트용 ansible 소스

## 1. Playbook 실행 방법(사전에 hosts에 host 정의 필수)

```shell
 # ansible-playbook -l {HOST_IP or HOST_GROUP_NAME} {PLAYBOOK_NAME} 
 $ ansible-playbook -l DB playbook/db/start_mysqld.yml # 방법1. HOST_IP 
 $ ansible-playbook -l 10.0.1.167 playbook/db/start_mysqld.yml # 방법2. HOST_GROUP_NAME
```

## 2. Playbook 시연
* Playbook 실행 위치는 `/home/ec2-user/ktds-MSP-ansible`
* `/home/ec2-user/ktds-MSP-ansible` 경로로 이동

```shell
$ cd /home/ec2-user/ktds-MSP-ansible
```
### 2.1 Host 확인
 * Target Host가 Host 파일에 등록되었는지 확인
```shell
$ cat /etc/ansible/hosts 
[DB]
10.0.1.167	ansible_user=anaws

[WEB]
10.0.2.141	ansible_user=anaws
```

### 2.2 DB 

 * DB 설치
```shell
 $ ansible-playbook -l 10.0.1.167 playbook/db/install_mysqld.yml
```

 * DB 삭제

```shell
 $ ansible-playbook -l 10.0.1.167 playbook/db/uninstall_mysqld.yml
```

 * DB 기동(오류 발생 시 DB설치가 되었는지 확인요망)

```shell
 $ ansible-playbook -l 10.0.1.167 playbook/db/start_mysqld.yml
```

 * DB 중지(오류 발생 시 DB설치가 되었는지 확인요망)

```shell
 $ ansible-playbook -l 10.0.1.167 playbook/db/stop_mysqld.yml
```

### 2.3 OS

 * 커널 파라미터 수정

```shell
 $ ansible-playbook -l 10.0.2.141 playbook/os/change_kernel_param.yml
```

 * OS 재기동

```shell
 $ ansible-playbook -l 10.0.2.141 playbook/os/reboot.yml
```


