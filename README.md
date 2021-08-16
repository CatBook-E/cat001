# heroku-vless
Deploy VLESS server to heroku

[![Deploy](https://www.herokucdn.com/deploy/button.png)](https://dashboard.heroku.com/new?template=https://github.com/CatBook-E/cat001/tree/main)

```
VLESS:
Address: yourAppName.herokuapp.com
Port: 443
id: Your entered id
Flow: xtls-rprx-direct
encryption: none
Transport: ws
TLS: tls

### 注意
#### 路径
WebSocket 路径(配置文件中的 path )为 `/app` 。

#### 端口
端口 为 `443` 。

#### alterId
alterId 为 `0`。

#### UUID
UUID 默认为 `3a53a3e5-da83-48d2-aee9-d88a498eb3dd` 可自行设置。

### 流量中转
可以使用cloudflare的workers来中转流量，配置为：

```
addEventListener(
  "fetch",event => {
    let url=new URL(event.request.url);
    url.hostname="xx.herokuapp.com";//你的heroku域名
    let request=new Request(url,event.request);
    event. respondWith(
       fetch(request)
    )
  }
)
