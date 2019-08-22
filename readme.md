## 如何屏蔽video中的全屏、画中画和下载按钮

#### 屏蔽全屏
1. 样式直接处理：
```
<style type="text/css">
	video::-webkit-media-controls-fullscreen-button { display: none; }
</style>
```

2. 给video标签添加属性：```controlsList="nofullscreen"```
---
#### 屏蔽画中画
https://www.itouchtv.cn/article/33fc2b36e32afd943558c74467dec4d6
1. html方式
    * 给video标签添加属性：```disablePictureInPicture```

```
<video data-pep-player src="http://192.168.186.60/jxw-web/p/resource/hlsIndexM3u8.token?resId=12110011011610205001542954347676" controls disablePictureInPicture></video>
```

2. js方式
```
var aVideos = document.querySelectorAll('video')
for(var i=0; i<aVideos.length; i++){
	aVideos[i].disablePictureInPicture = true
}
```
---
#### 屏蔽下载
video标签中添加属性：```controlslist="nodownload"```
> 官网说明：HTMLMediaElement.controlsList
HTMLMediaElement接口的controlsList 属性返回DOMTokenList，帮助用户在显示其自己的控件集时选择要在媒体元素上显示的控件。DOMTokenList可以设置以下三个可能值中的一个或多个：nodownload，nofullscreen和noremoteplayback。
https://developer.mozilla.org/zh-CN/docs/Web/API/HTMLMediaElement/controlsList

```
<video src="/i/movie.ogg" controls="controls" disablePictureInPicture controlslist="nodownload">
your browser does not support the video tag
</video
```

#### 屏蔽示例:
> https://googlechrome.github.io/samples/media/controlslist.html

---
#### 个人总结：
```
var aVideos = document.querySelectorAll('video')
for(var i=0; i<aVideos.length; i++){
	aVideos[i].setAttribute('controlslist', 'nofullscreen');  // 屏蔽视频中的全屏功能
	aVideos[i].disablePictureInPicture = true;   			// 屏蔽视频中的画中画功能
	aVideos[i].setAttribute('controlslist', 'nodownload');  // 屏蔽视频中的下载功能
}
```
