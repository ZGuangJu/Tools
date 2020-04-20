标准 Clash 配置文件

# 第一种配置
- name: "你的 SS 节点 1"               # 软件显示的节点名字
  type: ss                                  # 代理类型
  server: 1.2.4.8                          # 服务器 IP
  port: 443                                 #  端口号
  cipher: chacha20-ietf-poly1305   # 加密方法
  password: "password"                # SS 密码
  # udp: true                                #默认不开启
  
#第二种配置
# Shadowsocks + simple-obfs   配置范本
- name: "你的 SS 节点 2"
  type: ss
  server: 1.2.4.8
  port: 443
  cipher: chacha20-ietf-poly1305
  password: "password"
  plugin: obfs
  plugin-opts:                 
    mode: tls # or http               #  大部分选择 HTTP
    # host: bing.com                  #  伪装

v2ray 的标准写法

# VMess 的配置
- name: "你的 V2RAY 节点 1" # 软件显示的节点名字
  type: vmess # 代理类型
  server: v2rayssr.com  # 服务器 IP
  port: 443 #  端口号
  uuid: a3482e88-686a-4a58-8126-99c9df64b7bf
  alterId: 64  #额外的 ID
  cipher: auto
  #上面几行为必选参数
  #下面几行为可选参数  根据你的配置情况来
  # udp: true    #默认不开启
  # tls: true      #TLS 开启
  # skip-cert-verify: true     #默认不开启
  # network: ws    # 网路类型 WS HTTP 等
  # ws-path: /path  # 路径
  # ws-headers:     #默认不开启
  #  Host: v2rayssr.com    # HOST
  
  下面的代码是 v2ray+ws+tls(+nginx)的源码配置：
  
  - name: "主机测试"
  type: vmess
  server: www.v2rayssr.com
  port: 443
  uuid: dfdf8e0-c95d-4c74-b5d5-4a330969c8cb
  alterId: 2
  cipher: auto
  tls: true
  network: ws
  ws-path: /f2a5dfd0/
  Host: www.v2rayssr.com
  
  Trojan Clash/ClashX 配置文件写法
  
  # Trojan 的配置
  - name: "Trojan 节点测试"
    type: trojan
    server: server
    port: 443
    password: yourpsk
    # udp: true
    # sni: example.com # aka server name
    # alpn:
    #   - h2
    #   - http/1.1
    # skip-cert-verify: true
    
  以下是波仔搭建的一个 Trojan 的写法（供参考）
  
# 配置开始
- name: "Trojan 主机测试" # 软件显示的节点名字
  type: trojan
  server: hk.v2rayssr.com # 服务器域名
  port: 443
  password: trojanpasswords #Trojan 密码  
  

修改以下信息，大概在133行：

- name: "Trojan节点的主机测试"
  type: trojan
  server: xxx.xxxx.com
  # 服务器地址
  port: 443
  # 默认
  password: xxxxxxxxxx
  # 密码


###############################################################配置分割线
