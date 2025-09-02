![kenzo github stats](https://github-readme-stats.vercel.app/api?username=kenzok8&show_icons=true&theme=merko)
<div align="center">
<h1 align="center">同步上游分支代码</h1>
<img src="https://img.shields.io/github/issues/kenzok8/small-package?color=green">
<img src="https://img.shields.io/github/stars/kenzok8/small-package?color=yellow">
<img src="https://img.shields.io/github/forks/kenzok8/small-package?color=orange">
<img src="https://img.shields.io/github/license/kenzok8/small-package?color=ff69b4">
<img src="https://img.shields.io/github/languages/code-size/kenzok8/small-package?color=blueviolet">
</div>


#### small-package

*  本人亲测常用OpenWrt软件包源码合集，支持最新openwrt24.10！
*  关于有好的插件请在issues提交

*  感谢以上github仓库所有者！

#### 使用方式：

```bash
 sed -i '$a src-git smpackage https://github.com/liuxiaobing/small-package' feeds.conf.default
```
对于强迫症的同学（有报错信息、或Lean源码编译出错的情况），请尝试删除冲突的插件

```bash
rm -rf feeds/smpackage/{base-files,dnsmasq,firewall*,fullconenat,libnftnl,nftables,ppp,opkg,ucl,upx,vsftpd*,miniupnpd-iptables,wireless-regdb}
```
为了避免编辑出错，升级golang!

```bash
rm -rf feeds/packages/lang/golang
git clone https://github.com/sbwml/packages_lang_golang -b 24.x feeds/packages/lang/golang
```
更新了docker服务器设置!

```bash
删除openwrt自带的docker服务器设置插件
rm -rf feeds/luci/applications/luci-app-dockerman

./scripts/feeds update -a
./scripts/feeds install -a
```
如果编译openwrt时碰到这个问题了
```bash
要修改/home/你的用户名/openwrt/build_dir/target-x86_64_musl/host/rustc-1.xx.x-src/路径下面的Cargo.toml和config.toml，

Cargo.toml里面在第一行插入：

[source.crates-io]
replace-with = 'mirror'

[source.mirror]
registry = "sparse+https://mirrors.bfsu.edu.cn/crates.io-index/"

download-ci-llvm = false

原来的行下移。

修改config.toml:
download-ci-llvm = true
改成：
download-ci-llvm = false
```
