# v2rayXPlus
![](https://gitlab.com/xiayesuifeng/v2rayxplus/raw/master/resources/v2rayXPlus-64px.svg)

> 使用go写的v2ray gui客户端

[![pipeline status](https://gitlab.com/xiayesuifeng/v2rayxplus/badges/master/pipeline.svg)](https://gitlab.com/xiayesuifeng/v2rayxplus/commits/master)
[![Go Report Card](https://goreportcard.com/badge/gitlab.com/xiayesuifeng/v2rayxplus)](https://goreportcard.com/report/gitlab.com/xiayesuifeng/v2rayxplus)
[![GoDoc](https://godoc.org/gitlab.com/xiayesuifeng/v2rayxplus?status.svg)](https://godoc.org/gitlab.com/xiayesuifeng/v2rayxplus)
[![Sourcegraph](https://sourcegraph.com/gitlab.com/xiayesuifeng/v2rayxplus/-/badge.svg)](https://sourcegraph.com/gitlab.com/xiayesuifeng/v2rayxplus)

使用iptables+透明代理+v2ray路由实现真全局自动分流

感谢[@linyuan](t.me/linyuan)提供的logo


## Dependencies
[therecipe/qt](https://github.com/therecipe/qt.git)

## Install therecipe/qt

[https://blog.firerain.me/article/6](https://blog.firerain.me/article/6) or
[therecipe/qt install](https://github.com/therecipe/qt/wiki/Installation)

add $GOPATH/go/bin to environment variables

## Build or [v2rayxplus.zip](https://gitlab.com/xiayesuifeng/v2rayxplus/builds/artifacts/master/download?job=run-build) (qt5.11)

> bash
```
go get -t gitlab.com/xiayesuifeng/v2rayxplus

cd $(go env GOPATH)/src/gitlab.com/xiayesuifeng/v2rayxplus

qtrcc desktop ./resources/

qtdeploy build desktop 
```

> fish
```
go get -t gitlab.com/xiayesuifeng/v2rayxplus

cd (go env GOPATH)/src/gitlab.com/xiayesuifeng/v2rayxplus

qtrcc desktop ./resources/

qtdeploy build desktop 

```

# Install
vim /usr/lib/systemd/system/v2rayxplus.service
```
[Unit]
Description=V2RayXPlus Service
After=network.target
Wants=network.target

[Service]
Type=oneshot
ExecStart=/usr/bin/v2rayxplus -start
ExecStop=/usr/bin/v2rayxplus -stop
ExecStartPre=/usr/bin/systemctl start v2ray.service
ExecStopPost=/usr/bin/systemctl stop v2ray.service
RemainAfterExit=yes

[Install]
WantedBy=multi-user.target
```

```
sudo cp ./deploy/linux/v2rayxplus /usr/bin
sudo systemctl daemon-reload
```

## License

v2rayXPlus is licensed under [GPLv3](LICENSE).