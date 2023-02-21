# 最簡單手動安裝 Shadowsocks 方法
## 伺服器搭建 + 配置
### 安裝需求
1. 請確保你已經擁有 Root 權限 在 Terminal - 如果沒有，請輸入 "sudo su" 並輸入 Root 密碼。
2. 系統為 Ubuntu，版本為 16.04 以上。
### 安裝步驟
1. apt install shadowsocks - 安裝Shadowsocks，按 Y 以繼續
(可選) 2. systemctl status shadowsocks 以查看現在是否運行 Shadowsocks 服務，如果顯示為 "Active" (綠色字)，表示已經運行。
3. vi /etc/shadowsocks/config.json 修改配置文件，
#### 默認配置文件如下
```
{
    "server":"my_server_ip",
    "server_port":8388,
    "local_address": "127.0.0.1",
    "local_port":1080,
    "password":"mypassword",
    "timeout":300,
    "method":"aes-256-cfb",
    "fast_open": false
}
```
### 需要修改為如下的配置
```
{
    "server":"0.0.0.0",                         //設定為 0.0.0.0 代表所有 IP 可以訪問
    "server_port":8388,                       //Shadowsocks 端口
    "local_address": "127.0.0.1",
    "local_port":1080,
    "password":"test1234",           //請設置一個密碼作為連線
    "timeout":300,
    "method":"aes-256-cfb",
    "fast_open": false
}
```
4. 輸入 ":wq" 以保存並退出。
## 重要！！！ 5. 輸入 "systemctl restart shadowsocks" 以重啟 Shadowsocks。
