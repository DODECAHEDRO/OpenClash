# OpenClash
immortalwrt固件：https://firmware-selector.immortalwrt.org

openclash luci地址：https://github.com/vernesong/OpenClash

openclash核心地址：https://github.com/vernesong/OpenClash/tree/core/master

clashmeta官方核心地址：https://github.com/MetaCubeX/mihomo/tree/Alpha

adguardhome luci地址：https://github.com/kongfl888/luci-app-adguardhome/releases

adguardhome核心地址：https://github.com/kongfl888/luci-app-adguardhome/releases

订阅后端subconverter支持文档：https://github.com/tindy2013/subconverter/blob/master/README-cn.md

规则集地址：[ACL4SSR](https://github.com/ACL4SSR/ACL4SSR/tree/master/Clash)        [blackmatrix7](https://github.com/blackmatrix7/ios_rule_script/tree/master/rule/Clash)

规则文件：https://drive.google.com/drive/folders/1j2uMkA_R8ppINtKkQY78gJrBJjBPtJia

DNS泄露检测：[网站一](https://ipleak.net/)        [网站二](https://browserleaks.com/dns)


OpenClash Luci安装：

immortalwrt软件包处直接安装,  官方openwrt手动安装、Lean的固件请使用已经编译好openclash的固件。

命令安装注意事项：
首先分辨openwrt防火墙类别（iptables or nftables）、

通过ssh连接openwrt执行命令判断：
iptables -L
如果能正常列出规则,则表示使用的是iptables
nft list ruleset
如果能正常列出规则,则表示使用的是nftables
官方openwrt固件：OpenWrt 22.03系列专注于从基于iptables的防火墙3迁移到基于nftables的防火墙4
immortalwrt固件：过渡版本两者共存  默认使用nftables  最新版也单独使用nftables
Lean固件：iptables
分辨后再根据对应的防火墙类别安装对应的依赖（阅读下面的注意事项再安装），然后安装Luci文件。

注意:如果安装依赖过程中有关于dnsmasq-full 的报错，一般是因为OpenClash 其中一项依赖是 dnsmasq-full，openwrt固件有的默认的是dnsmasq（可在已安装包中确认），需要删除dnsmasq再安装dnsmasq-full 。
opkg remove dnsmasq       卸载dnsmasq  安装依赖前执行卸载.
opkg remove dnsmasq && opkg install dnsmasq-full  卸载dnsmasq并安装dnsmasq-full,如果忘记卸载dnsmasq安装依赖后报错,执行这个.

openclash安装clash内核
第一方案：如果openwrt 有其他的科学插件例如passwall可以正常使用，开启后直接点击更新即可，更新完毕记得关闭。
第二方案：电脑端目前可以正常翻墙例如使用clash v2ray等，直接点击下载到本地或者下载官方版本，然后手动上传安装。
第三方案：如果目前没有科学环境，使用选择CDN下载更新，耐心等待！！
