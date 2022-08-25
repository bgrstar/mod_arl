## ARL(Asset Reconnaissance Lighthouse)资产侦察灯塔系统

- https://github.com/TophantTechnology/ARL 修改了一点东西自用系列（抄）。
- 整理的一份指纹：https://github.com/bgrstar/Tools/blob/main/rules.json，导入即可用
- 想看代码自己进docker或如上原项目地址看哈

### 0x00 简介

在开始使用之前，请务必阅读并同意[免责声明](Disclaimer.md)中的条款，否则请勿下载安装使用本系统。


### 0x01 系统要求

目前暂不支持Windows。Linux和MAC建议采用Docker运行，系统配置最低2核4G。  
由于自动资产发现过程中会有大量的的发包，建议采用云服务器可以带来更好的体验。  

### 0x02 Docker 启动

```
git clone https://github.com/bgrstar/mod_arl
cd mod_arl/docker/
htpasswd -c htpasswd 用户名
docker volume create arl_db
自行配置config-docker.yaml里面的内容
docker-compose pull
docker-compose up -d 
```

### 0x03 配置密码密码重置

当忘记了登录密码，可以执行下面的命令，然后使用 `admin/admin123` 就可以登录了。
```
docker exec -ti arl_mongodb mongo -u admin -p admin
use arl
db.user.drop()
db.user.insert({ username: 'admin',  password: hex_md5('arlsalt!@#'+'admin123') })
```
URL：https://127.0.0.1:5003
网页访问账号密码如htpasswd设置


### 0x04 FAQ

请访问如下链接[FAQ](https://github.com/TophantTechnology/ARL/wiki/Docker-%E7%8E%AF%E5%A2%83%E5%AE%89%E8%A3%85-ARL#faq)

### 0x05 写在最后

目前ARL仅仅只是完成了对资产的部分维度的发现和收集，自动发现过程中难免出现覆盖度不全、不精准、不合理等缺陷的地方还请反馈至我们。  
