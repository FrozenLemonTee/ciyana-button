![ciyana.jpg](https://i.loli.net/2021/03/26/2bug1tn9AfsqUNG.jpg)
# 💤梦魇按钮/Ciyana Button💤

**这是一只哭包梦魇——希亚娜的音声合集网站，收集了希亚娜平时直播时的各种音声片段**

**按钮传送门：https://ciyana.moe/**

### 参与网站建设

参与翻译、添加语音等可以选择Fork项目：

添加语音文件需要同时改动语音信息文件，如下：

语音信息文件路径:

> `setting/translate/01_voices.json`

具体格式：

```json
    {
    "name": "希希不会是个天才吧",
    "path": "希希不会是个天才吧.mp3",
    "date": "2021-03-20",
    "translate": {
      "zh-CN": "希希不会是个天才吧",
      "en-US": "I'm a genius"
    },
    "category": "可爱希",
    "mark": {
      "title": "堂堂梦魇，今日出道！【希亚娜Ciyana首播剪辑】",
      "time": "16:43-16:46 1P",
      "url": "https://www.bilibili.com/video/BV1EA411M7z6"
    }
  }
```

其中，`path`指的是对应的音频文件名，存放在`public/voices`，推荐使用MP3格式。`translate`下的为该语音的中文和英文标题，请不要和`name`相混淆。`category`指明默认显示下该音声归于哪一类，需要根据分类信息文件进行改动，如下：

分类信息文件路径:

> `setting/translate/category.json`

具体格式：

```json
  {
    "name": "可爱希",
    "translate": {
      "zh-CN": "可爱希",
      "en-US": "cute Ciyana"
    }
  }
```

提出问题和意见也可以选择在issue反馈，或者在[b站](https://space.bilibili.com/88488273/)私信我

### LICENSE

- 使用[voices-button-cli](https://github.com/blacktunes/voices-button-cli)创建的语音按钮
- 所用模板为[Hiiro按钮](https://github.com/blacktunes/hiiro-button)

### 友情链接
- [Vtuber按钮合集](https://vtbbtn.org/)
- [猫猫按钮](https://hiiro.club/)（Hiiro）
- [豹按钮](https://haruka.cmyr.ltd/)（白神遥）
- [七奈按钮](https://kaguranana-button-blacktunes.vercel.app/)（神乐七奈）
- [京华破防站](https://kyouka.icu/)（京华 from Overidea）
- [Eliro按钮](https://eliro.top/)（彼岸霜滢）
- [虚研社按钮](https://eliro.top/)

### 更新日志
<details>
    <summary>点此展开</summary>
    - 2022/11/05
    <br>添加「Eliro按钮」、「虚研社按钮」友情链接<br> 
    - 2021/07/07
    <br>网页样式更新<br>    
    - 2021/07/04
    <br>新增84条语音<br>    
    - 2021/06/26
    <br>添加「京华破防站」友情链接<br>
    - 2021/03/28
    <br>添加「七奈按钮」友情链接<br>
    - 2021/03/23
    <br>添加「豹按钮」友情链接<br>
    - 2021/03/20
    <br>新增100条语音<br>
    添加「猫猫按钮」友情链接<br>
</details>