# vless-heroku
## If you can continue to use it, please keep a low profile. 
## Do not promote any website
## 如果能继续使用的，请保持低调！！！
## ![捕获1](https://user-images.githubusercontent.com/72486732/132205566-238ff619-6e57-4379-aa74-089d3a582d44.PNG) Fork本项目后将readme.md中的Dimitri2020007替换为自己的用户名后再进行部署，非常重要，切记！！！！
## 禁止在任何网站宣传本项目！！！！
## 带有删除线的部分表示不适用或已经废弃
## 自2021.11.18起不再部署caddy，改为单一vless部署以减少项目大小，提高项目稳定性。

## Deploy vless on heroku

## Fork this project, replace Dimitri2020007 in readme.md with your own user name before deploying, it is very important, remember!!!!
## The part with a strikethrough indicates that it is not applicable or has been obsoleted
## It is forbidden to promote this project on any website!!!!
## Since 2021.11.18, caddy will no longer be deployed, but a single vless deployment will be used to reduce project size and improve project stability.

[![Deploy](https://www.herokucdn.com/deploy/button.png)](https://dashboard.heroku.com/new?template=https://github.com/yanghuan/vless-heroku.git)

# VLESS Client Setup

| Connection Variables | Values |
| -------------------- | ------ |
| `Address` | yourAppName.herokuapp.com </br> Cloudflare Reverse Proxy IP |
| `SNI` | none |
| `AllowInsecure` | false |
| `Port` | 443 |
| `Host` | yourAppName.herokuapp.com </br> Cloudflare Reverse Proxy Domain Name |
| `Path` | /$ID-vless |
| `id` | Generate using UUID generator or V2RayN/V2RayNG client generate </br> [uuidgenerator](https://www.uuidgenerator.net/) |
| `Flow` | none |
| `encryption` | none |
| `Transport` | ws |
| `Tls` | Tls must open, otherwise your network was insecure! |

# Client Ws+Tls+Xtls-rprx-direct(Flow) Support Status
| Client | Status |
| ------ | ------ |
| `2dust V2RayN` </br> `2dust V2RayNG` | Ws+Tls+Flow |
| `OpenWrt SSRPlus` | Ws+Tls |
| `OpenWrt Passwall` | Ws+Tls |
| ~~`QV2Ray`~~ | ~~Ws+Tls~~ |

# Cloudflare Reverse Proxy Code (Choose one from both examples)

example 1
```
addEventListener(
  "fetch", event => {
    let url = new URL(event.request.url);
    url.host = "appname.herokuapp.com";
    let request = new Request(url, event.request);
    event.respondWith(
      fetch(request)
    )
  }
)
```

example 2 (recommend)
```
const SingleDay = 'appname.herokuapp.com'
const DoubleDay = 'appname.herokuapp.com'
addEventListener(
    "fetch",event => {
    
        let nd = new Date();
        if (nd.getDate()%2) {
            host = SingleDay
        } else {
            host = DoubleDay
        }
        
        let url=new URL(event.request.url);
        url.hostname="appname.herokuapp.com";
        let request=new Request(url,event.request);
        event. respondWith(
            fetch(request)
        )
    }
)
```

# Acknowledgments

- [Project V](https://github.com/v2fly/v2ray-core.git)
- [Project X](https://github.com/XTLS/Xray-core.git)
- [HeroKu](https://heroku.com)
- [heroku-vless](https://github.com/DanyTPG/heroku-vless.git)
- [CloudflareSpeedTest](https://github.com/XIU2/CloudflareSpeedTest.git)
- [Better Cloudflare IP](https://github.com/badafans/better-cloudflare-ip.git)

# Important information

New users only need to modify the id

Abuse is strictly prohibited, I am not responsible for all problems arising from abuse, and use and cherish!

This project is not suitable for long-term use over the wall.

For security reasons, please use cdn instead of custom domain names to achieve VLESS+WS+TLS.

It is forbidden to promote this project on any website!!!!
