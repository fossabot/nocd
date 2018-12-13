# NoCD 持续交付系统

[![Go Report Card](https://goreportcard.com/badge/github.com/naiba/nocd)](https://goreportcard.com/report/github.com/naiba/nocd) [![Build Status](https://travis-ci.com/naiba/nocd.svg?branch=master)](https://travis-ci.com/naiba/nocd) [![FOSSA Status](https://app.fossa.io/api/projects/git%2Bgithub.com%2Fnaiba%2Fnocd.svg?type=shield)](https://app.fossa.io/projects/git%2Bgithub.com%2Fnaiba%2Fnocd?ref=badge_shield)
 [![MIT license](https://img.shields.io/badge/license-MIT-brightgreen.svg)](http://opensource.org/licenses/MIT)  [![Version](https://img.shields.io/github/release/naiba/nocd/all.svg)](https://github.com/naiba/nocd/releases)

**NoCD** 是一个 Go 实现的轻便可控的持续交付系统。


[![FOSSA Status](https://app.fossa.io/api/projects/git%2Bgithub.com%2Fnaiba%2Fnocd.svg?type=large)](https://app.fossa.io/projects/git%2Bgithub.com%2Fnaiba%2Fnocd?ref=badge_large)

## 界面预览

| ![首页截图](https://github.com/naiba/nocd/raw/master/README/首页截图.png) | ![服务器管理](https://github.com/naiba/nocd/raw/master/README/服务器管理.png) | ![项目管理](https://github.com/naiba/nocd/raw/master/README/项目管理.png) |
| ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| ![交付记录](https://github.com/naiba/nocd/raw/master/README/交付记录.png) | ![管理中心](https://github.com/naiba/nocd/raw/master/README/查看日志.png) | ![查看日志](https://github.com/naiba/nocd/raw/master/README/管理中心.png)  |

## 系统特色

- 服务器：可以添加多个部署服务器。
- 项目：支持解析 Gogs、GitHub、Gitlab、BitBucket 的 WebHook
- 通知：部署成功或失败经 `Server酱` 推送到您的微信
- 交付记录：可以查看部署记录，用户可以停止部署中的流程
- 管理面板：查看系统状态，管理用户，管理部署中的流程


## 部署教程

1. Clone 源代码

2. 进入应用目录 `nocd/cmd/web`

3. 打包资源文件并编译

   ```shell
   go get -u github.com/tmthrgd/go-bindata/...
   go-bindata resource/...
   go build
   ```

4. 在 `conf/app.ini` 创建配置文件

   ```ini
   [nocd]
   cookie_key_pair = example
   debug = true
   domain = mjj.cx
   web_listen = 0.0.0.0:8000
   loc = Asia/Shanghai
   google_analysis = "NB-XXXXXX-1"
   [third_party]
   github_oauth2_client_id = example
   github_oauth2_client_secret = example
   sentry_dsn = "https://example:xx@example.io/"
   ```

5. 运行

   ```shell
   ./web
   ```

6. 在 `GitHub` 设置回调：`http://mjj.cx/oauth2/callback`

## 常见问题

1. 为什么我的部署脚本总是执行失败 或者 根本没有执行？<br>
  `请检查您的 PATH 路径是否引入，建议提前 export 一下路径，自动部署的时候不会 source .bash_profile 。`

2. 如何保持后台运行？<br>
  `可以使用 systemd 。`


## 版权声明

本仓库代码遵循 MIT 协议

Copy &copy; 2018 Naiba