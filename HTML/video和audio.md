#### video

```
const oV = document.querySelector("video");
oV.onplay = function(){
    console.log("视频开始播放时触发")；
    console.log(this.duration);//获取视频的总时间，单位是秒
}
oV.onpause = function(){
    console.log("视频播放暂停了");
}
oV.ontimeupdate = function(){
    console.log(this.currentTime);//当前播放的时间
}
oV.onended = function(){
    console.log("按照播放默认怎么播放","播放结束了")；
}
oV.ended;//是否结束，结束返回true
```

#### audio

  