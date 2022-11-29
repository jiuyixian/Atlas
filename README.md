# Atlas

## 这是什么
Atlas是一个适用于V3版本及以上Yunzai-Bot的图鉴插件包，可通过Yunzai-Bot查询[`米游社@西北壹枝花`](https://bbs.mihoyo.com/ys/accountCenter/postList?id=289918413)制作的原神(Genshin Impact)游戏图鉴。

插件代码严格遵循ES6规范。

关于介绍内容，可前往[Genshin-Atlas](https://gitee.com/Nwflower/genshin-atlas)查看
## 如何获取
### 1、下载插件本体
使用github获取
在Yunzai-Bot根目录下，运行
```
git clone --depth=1 https://github.com/Nwflower/atlas ./plugins/Atlas/
```

使用gitee镜像源
```
git clone --depth=1 https://gitee.com/Nwflower/atlas ./plugins/Atlas/
```

### 2、获取图片资源
安装插件后，发送`#图鉴升级`获取图鉴图片即可正常使用。

代码部分的更新请使用yunzai自带的`#全部更新`来更新本插件。

本插件非传统性质的plugin插件包，占用内存较少。

### 3、拓展：修改图鉴匹配规则（可以不修改）
如果你对当前图鉴匹配效果不满意，可以修改图鉴匹配规则以让插件更频繁或更少触发

规则文件在`resource/rule/对应文件夹目录名.yaml`里查看，如不存在对应文件夹目录名（例如圣遗物artifact的对应yaml不存在，则以默认config.yaml为准）

规则文件中，`mode`为匹配模式。
以口令`#雾切之回光`为例：
1. 当模式为不完全匹配（mode:1）时，`#雾切``#回光``#雾切之回光`均视为该口令，`#雾切之回光是什么武器`不视为该口令。
2. 当模式为完全匹配（mode:1）时，`#雾切之回光是什么武器``#神里面板换雾切之回光`均视为该口令，`#回光``#雾切之回光`不视为该口令。
3. 当模式为等同匹配（mode:1）时，仅`#雾切之回光`视为该口令。

规则文件中，`condition`为正则条件。
仍以图片`雾切之回光.png`为例，想要发送该图片:
1. 当条件为直接匹配（condition:0）时,口令`雾切之回光`才能发送该图片。
2. 当条件为`前缀#`（condition:1）时,口令`#雾切之回光`才能发送该图片，`雾切之回光`不能发送该图片。
3. 当条件为任意关键词（condition:2）时,需要配置关键词列表（pick）。若以默认关键词`图鉴`为例,口令`图鉴雾切之回光``雾切之回光图鉴`能发送该图片，`雾切之回光``#雾切之回光`不能发送该图片，因为它们不包含关键词。
4. 当条件为1或2（condition:3）时。满足条件1或满足条件2时都能发送该图片。除此之外，`#雾切之回光图鉴`也能发送该图片，但是当（condition=1或2）时，该口令不能正常触发。
5. 当条件为1且2（condition:4）时。满足条件1的情况下还要满足条件2时才能发送该图片。如`#雾切之回光图鉴``#图鉴雾切之回光`才能发送该图片，只满足一个不能正常触发。

规则文件中，`pick`为关键词列表
1. 关键词列表只在（condition>=2）的时候才会生效。当没有配置关键词列表，则默认为“图鉴”。
2. 以七圣召唤的规则（card.yaml）为例，pick中含有两词，分别为`七圣`和`牌`，又因为condition==2，所以如果要发送图片`凯瑟琳.png`，你必须使用口令`七圣凯瑟琳``凯瑟琳牌`才能发送该图片。
3. 第2点中，口令`#七圣凯瑟琳``#凯瑟琳牌`均不能发送该图片。
4. 最终口令只与去掉关键词和前缀#的实际词语有关，而与关键词的位置、个数、种类无关。比如第2点中，口令`凯七圣瑟琳``七圣凯瑟琳七圣牌`均能发送该图片。

特殊情况说明
1. 你可能会发现，即使你的规则为等同匹配，`#雾切`也能够触发图片`雾切之回光`，这是因为在别名文件`resource/othername/对应文件夹目录名.yaml`中，雾切之回光的别名含有雾切。所以，`#雾切`正确匹配的是`雾切`，`雾切`相当于`雾切之回光`，故而最终发送了`雾切之回光`的图片。
2. `前缀#`只在（condition=1、3或4）的时候才会生效，否则将视为你文件名的一部分。

## 致谢
| Nickname| Contribution |
|---------|------|
| [xiaoyao-cvs-plugin](https://gitee.com/Ctrlcvs/xiaoyao-cvs-plugin) | 参考武器、圣遗物别名 |
| [Yunzai-Bot小飞插件](https://gitee.com/xfdown/xiaofei-plugin) | 参考消息发送风控处理代码 |

## 其他
最后给个star或者[爱发电](https://afdian.net/a/Nwflower)，你的支持不会获得额外内容，但会提高本项目的更新积极性

严禁用于任何商业用途和非法行为

点击加入[Atlas交流群](https://qm.qq.com/cgi-bin/qm/qr?k=XOTZhBWpv68F1sfsMIzKJpg28NBPKJgg&jump_from=webapi&authKey=/XagQoLiUhOi+t67MCkWOSRLlXe+ywVmrkCHdoD3CjwqNzAUYspTrqYklkwb3W0R)
### 发电榜
| 名单| 发电量 |
|---------|------|
| 杨花洛尽 | 23.3 |
| 归来？汐去 | 20   |
| 寮青   | 15   |
| 薛皮皮| 5 |