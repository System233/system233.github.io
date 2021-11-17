# 风物之诗琴


## 乐谱文件格式

当前支持json和zip格式

### Json格式
```json
{
  "bpm": 80,                //每分钟节拍数，拍号始终为4/4
  "cover":"[URL,DataURL]",  //封面图片，可以为URL，也可以为DataURL
  "media":"[URL,DataURL]",  //乐谱背景，可以为URL，也可以为DataURL
                            //格式可以为图片，也可以是视频[未测试]
  "name": "乐谱ID",         //相同ID的乐谱是为同一乐谱，导入时将被覆盖
  "notes": [
    {
      "beat": 2,            //音符时值:1 2 4 8 16 32
                            //分别代表:1/1 1/2 1/4 1/8 1/16 1/32秒
                            //过长的音符请用休止符替代
      "id": "ZXCVBNMASDFGHJQWERTYU-" //当前按下的键,-为休止符
    }
  ],
  "title": "乐谱标题",       //乐谱的显示名称
  "type": "windsong",       //乐谱类型[暂时没用]
  "version": 1              //乐谱版本[暂时没用]
}
```
### Zip格式
zip格式只是把json中的`cover`和`media`做分离打包，避免DataURL把json撑太大  
zip中的json文件名必须为`meta.json`, json中的`cover`和`media`属性可以使用zip中的文件路径，如`cover.png`。
```ls
.zip
 |-meta.json
 |-cover.png
 |-media.png
```
