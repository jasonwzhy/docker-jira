# 基于docker 的jira 安装及破解
1. 下载docker-compose.yaml文件

```
wget https://raw.githubusercontent.com/joker8023/jira/master/docker-compose.yaml
```
2. 启动docker-compose


```
sudo docker-compose up -d
```

3. 破解 jira

[破解文件](http://pan.baidu.com/s/1dEXwA21) 密码：d10q
破解文件和中文包都在里面 

3.1 进入jira
```
sudo docker exec -it jira /bin/sh
```
3.2 备份文件


```
mv /opt/atlassian/jira/atlassian-jira/WEB-INF/lib/atlassian-extras-2.2.2.jar /opt/atlassian/jira/atlassian-jira/WEB-INF/lib/atlassian-extras-2.2.2.jar.bak
```
atlassian-universal-plugin-manager-plugin的版本可能不一致,按照实际情况备份
```
 mv /opt/atlassian/jira/atlassian-jira/WEB-INF/atlassian-bundled-plugins/atlassian-universal-plugin-manager-plugin-2.19.1.jar /opt/atlassian/jira/atlassian-jira/WEB-INF/atlassian-bundled-plugins/atlassian-universal-plugin-manager-plugin-2.19.1.jar.bak

```
3.3 将破解文件复制到相应位置
我的破解文件在 /home/gench/下

```
sudo docker cp /home/gench/atlassian-extras-2.2.2.jar jira:/opt/atlassian/jira/atlassian-jira/WEB-INF/lib/atlassian-extras-2.2.2.jar
```
破解文件atlassian-universal-plugin-manager-plugin 可能版本不一样，改名字成你自己的版本名字然后复制
```
docker cp /home/gench/atlassian-universal-plugin-manager-plugin-2.19.1.jar jira:/opt/atlassian/jira/atlassian-jira/WEB-INF/atlassian-bundled-plugins/atlassian-universal-plugin-manager-plugin-2.19.1.jar
```
3.4 重启docker

```
sudo docker stop jira
sudo docker start jira
```
3.5 
设置 -系统 -授权
输入

```
Description=JIRA: Commercial,
CreationDate=2017-03-25,
jira.LicenseEdition=ENTERPRISE,
Evaluation=false,
jira.LicenseTypeName=COMMERCIAL,
jira.active=true,
licenseVersion=2,
MaintenanceExpiryDate=2099-12-31,
Organisation=GENCH,
SEN=SEN-L9480575,
ServerID=BTTV-B5E7-W7QX-ZYT0,
jira.NumberOfUsers=-1,
LicenseID=LIDSEN-L2651368,
LicenseExpiryDate=2099-12-31,
PurchaseDate=2017-05-25,
```
Organisation改成你自己的组织，可以随便写
SEN ，ServerID在授权信息上有的，改掉 确定就可以了







