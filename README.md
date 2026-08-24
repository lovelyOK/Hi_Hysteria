### 拉取安装

```
su - root #switch to root user.
bash <(curl -fsSL https://raw.githubusercontent.com/lovelyOK/Hi_Hysteria/main/server/install.sh)
```

### 配置过程

首次安装后: `hihy`命令调出菜单,如更新了hihy脚本，请执行选项 `9`或者 `12`,获得最新的配置

```
 -------------------------------------------
|**********      Hi Hysteria       **********|
|**********    Author: emptysuns   **********|
|**********     Version: 0.4.6     **********|
 -------------------------------------------
Tips:hihy 命令再次运行本脚本.
............................................. 
############################### 

..................... 
1)  安装 hysteria 
2)  卸载 
..................... 
3)  启动 
4)  暂停 
5)  重新启动 
6)  运行状态 
..................... 
7)  更新Core 
8)  查看当前配置 
9)  重新配置 
10) 切换ipv4/ipv6优先级 
11) 更新hihy 
12) 完全重置所有配置 
13) 修改当前协议类型
14) 查看实时日志

############################### 


0)退出 
............................................. 
请选择:
```

**脚本每次更新都可能会发生改变，请一定要展开并仔细参考演示过程，避免发生不必要的错误！**

<details>
  <summary>演示较长，点我查看</summary>
<pre><blockcode> 
开始配置:
请选择证书申请方式:

1、使用ACME申请(推荐,需打开tcp 80/443)
2、使用本地证书文件
3、自签证书

输入序号:
3
请输入自签证书的域名(默认:wechat.com):
注意:自签证书近一段时间来遭到大量随机阻断,请谨慎使用(这条提示不消失说明阻断还在继续)
如果一定要使用自签证书,请在下方配置选择使用obfs混淆验证,保证安全性
fuck.qq.com
判断自签证书,客户端连接所使用的地址是否正确?公网ip:1.2.3.4
请选择:

1、正确(默认)
2、不正确,手动输入ip

输入序号:
1

->您已选择自签fuck.qq.com证书加密.公网ip:1.2.3.4

选择协议类型:

1、udp(QUIC,可启动端口跳跃)
2、faketcp
3、wechat-video(默认)

输入序号:
3

->传输协议:wechat-video

请输入你想要开启的端口,此端口是server端口,建议10000-65535.(默认随机)

->使用随机端口:udp/14274

请输入您到此服务器的平均延迟,关系到转发速度(默认200,单位:ms):
180

->延迟:180 ms

期望速度,这是客户端的峰值速度,服务端默认不受限。Tips:脚本会自动*1.10做冗余，您期望过低或者过高会影响转发效率,请如实填写!
请输入客户端期望的下行速度:(默认50,单位:mbps):
180

->客户端下行速度：180 mbps

请输入客户端期望的上行速度(默认10,单位:mbps):
30

->客户端上行速度：30 mbps

请输入认证口令(默认随机生成,建议20位以上强密码):

->认证口令:Wvb9NlmWt0BxkJXoLnYKvM0NoOUz6sIgdaWHDr1gMzQGtE8lIs

Tips: 如果使用obfs混淆加密,抗封锁能力更强,能被识别为未知udp流量,但是会增加cpu负载导致峰值速度下降,如果您追求性能且未被针对封锁建议不使用
选择验证方式:

1、auth_str(默认)
2、obfs

输入序号:
2

->您选择的验证方式为:obfs

请输入客户端名称备注(默认使用域名/IP区分,例如输入test,则名称为Hys-test):
demo

配置录入完成!

执行配置...
SIGN...

Signature ok
subject=C = CN, ST = GuangDong, L = ShenZhen, O = PonyMa, OU = Tecent, emailAddress = admin@qq.com, CN = Tencent Root CA
Getting CA Private Key
rm: cannot remove '/etc/hihy/cert/fuck.qq.com.ca.srl': No such file or directory
SUCCESS.

net.core.rmem_max = 8000000

Test config...

IPTABLES OPEN: udp/14274
Test success!
Generating config...
安装成功,请查看下方配置详细信息
docker.sh: line 877: 27670 Killed                  /etc/hihy/bin/appS -c /etc/hihy/conf/hihyServer.json server > /tmp/hihy_debug.info 2>&1

1* [v2rayN/nekoray] 使用hysteria core直接运行:
客户端配置文件输出至: /root/Hys-demo(v2rayN).json ( 直接下载生成的配置文件[推荐] / 自行复制粘贴下方配置到本地 )
Tips:客户端默认只开启http(8888)、socks5(8889)代理!其他方式请参照hysteria文档自行修改客户端config.json
↓***********************************↓↓↓copy↓↓↓*******************************↓
{
"server": "1.2.3.4:14274",
"protocol": "wechat-video",
"up_mbps": 33,
"down_mbps": 198,
"http": {
"listen": "127.0.0.1:10809",
"timeout" : 300,
"disable_udp": false
},
"socks5": {
"listen": "127.0.0.1:10808",
"timeout": 300,
"disable_udp": false
},
"obfs": "Wvb9NlmWt0BxkJXoLnYKvM0NoOUz6sIgdaWHDr1gMzQGtE8lIs",
"auth_str": "",
"alpn": "h3",
"acl": "acl/routes.acl",
"mmdb": "acl/Country.mmdb",
"server_name": "fuck.qq.com",
"insecure": true,
"recv_window_conn": 18612224,
"recv_window": 74448896,
"disable_mtu_discovery": true,
"resolver": "https://223.5.5.5/dns-query",
"retry": 3,
"retry_interval": 3,
"quit_on_disconnect": false,
"handshake_timeout": 15,
"idle_timeout": 30,
"fast_open": true,
"hop_interval": 120
}
↑***********************************↑↑↑copy↑↑↑*******************************↑

2* [Shadowrocket/Sagernet/Passwall] 一键链接:
hysteria://1.2.3.4:14274?protocol=wechat-video&auth=&obfsParam=Wvb9NlmWt0BxkJXoLnYKvM0NoOUz6sIgdaWHDr1gMzQGtE8lIs&peer=fuck.qq.com&insecure=1&upmbps=33&downmbps=198&alpn=h3#Hys-demo

3* [Clash.Meta] 配置文件已在/root/Hys-demo(clashMeta).yaml输出,请下载至客户端使用(beta)

`</blockcode></pre>`

</details>

