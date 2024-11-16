# cf-api-v4-ddns
CloudFlare 一键 ddns 脚本

下载cf-v4-ddns.sh编辑一下加到crontab里就完事了

curl https://raw.githubusercontent.com/noir1216/cf-api-v4-ddns/master/cf-v4-ddns.sh > /root/cf-v4-ddns.sh && chmod +x /root/cf-v4-ddns.sh

修改default config下的几个配置变量
其中CFTOKEN填的是API Token，中文叫API令牌，别填了下面的API Key

crontab -e

在最后加上*/2 * * * * /root/cf-v4-ddns.sh >/dev/null 2>&1
如果需要日志就换成这条*/2 * * * * /root/cf-v4-ddns.sh >> /var/log/cf-v4-ddns.log 2>&1
