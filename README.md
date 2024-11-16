# cf-api-v4-ddns
CloudFlare 一键 ddns 脚本<br>
下载cf-v4-ddns.sh编辑一下加到crontab里就完事了

### 下载 DNNS 脚本
    curl https://raw.githubusercontent.com/noir1216/cf-api-v4-ddns/master/cf-v4-ddns.sh > /root/cf-v4-ddns.sh && chmod +x /root/cf-v4-ddns.sh



### 修改 DDNS 脚本并补充相关信息
    # incorrect api-key results in E_UNAUTH error
    # 填写 Global API Key
    CFKEY=

    # Username, eg: user@example.com
    # 填写 CloudFlare 登陆邮箱
    CFUSER=

    # Zone name, eg: example.com
    # 填写需要用来 DDNS 的一级域名
    CFZONE_NAME=

    # Hostname to update, eg: homeserver.example.com
    # 填写 DDNS 的二级域名(只需填写前缀)
    CFRECORD_NAME=

### 设置定时任务
首次运行脚本,输出内容会显示当前IP，进入cloudflare查看 确保IP已变更为当前IP<br>
###
    ./cf-v4-ddns.sh


定时任务<br>
###
    crontab -e
    */2 * * * * /root/cf-v4-ddns.sh >/dev/null 2>&1
    #如果需要日志，替换上一行代码
    */2 * * * * /root/cf-v4-ddns.sh >> /var/log/cf-ddns.log 2>&1

