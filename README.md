# something
未完成的编辑 请勿随机使用

个人用Surge Panel脚本

由于panel脚本需要根据个人情况进行自定义，因此不再提供模组，请将需要的部分截取建立为本地模组并修改使用

使用效果：

#!name=Panels

#!desc=信息面板

[Panel]
#Surge Pro标题,可显示启动时间,点击刷新为重载配置

SurgePro_ ReloadProfile = script-name=SurgePro_ ReloadProfile,update-interval=1

#流量统计

TrafficStatistics = script-name=TrafficStatistics,update-interval=1

NET_info = script-name=NET_info,update-interval=1

Sub_info = script-name=Sub_info,update-interval = 43200

NetflixSelect = script-name=NetflixSelect, update-interval=3600

groupPanelMaster= script-name=groupPanelMaster,update-interval=5



[Script]

#重载配置,Surge Pro标题,可显示启动时间,点击刷新为重载配置

SurgePro_ ReloadProfile = type=generic,timeout=10,script-path= https://raw.githubusercontent.com/fishingworld/something/main/PanelScripts/surgepro_reloadprofile.js ,argument=icon=crown.fill&color=#f6c970

#流量统计
#必须更改的字段:inter en0为WiFi pdp_ip0为卡1 pdp_ip1为卡2

TrafficStatistics = type=generic,timeout=10,script-path=TrafficStatistics.js,argument=icon=arrow.up.arrow.down.circle&color=#5d84f8

#網路詳情 标题显示为根节点名

#流量统计

#应当修改的字段：network 填写en0为WiFi pdp_ip0为卡1 pdp_ip1为卡2

TrafficStatistics = type=generic,timeout=10,script-path= https://raw.githubusercontent.com/fishingworld/something/main/PanelScripts/trafficstatistics.js ,argument=icon=arrow.up.arrow.down.circle&color=#5d84f8&network=en0

#流量信息

#必须添加的字段:你encode后的机场订阅链接
Sub_info = type=generic,timeout=10,script-path=https://raw.githubusercontent.com/mieqq/mieqq/master/sub_info_panel.js ,script-update-interval=0,argument=url=[URL encode 后的机场节点链接]&reset_day=1&title=title=ExFlux&icon=opticaldisc&color=#5AC8FA

#策略组面板

#必须更改的字段：group 填写需要显示的策略组名称
groupPanelMaster = type=generic,timeout=10,script-path=groupPanel.js,argument=icon=network&color=#86abee&group=Master

#netflix策略组控制
#必须更改的字段 netflixGroup 填写你Netflix策略组名称
#详情请阅读：https://github.com/fishingworld/something/blob/main/NetflixSelect/README.md

NetflixSelect = type=generic, script-path=https://raw.githubusercontent.com/fishingworld/something/main/NetflixSelect/nf_autoselect.js, argument=icon1=checkmark.circle&color1=#55ba94&icon2=checkmark.circle.trianglebadge.exclamationmark&color2=#9a9ced&icon3=hand.raised.circle&color3=#ea5532&netflixGroup=Netflix

NetflixChecker = type=cron,cronexp=5 4 * * *,wake-system=1,timeout=3600,script-path=https://raw.githubusercontent.com/fishingworld/something/main/NetflixSelect/nf_autocheck.js ,script-update-interval=0,control-api=1
