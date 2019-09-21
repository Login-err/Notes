##### 常见的文件下载

使用a标签``<a href="文件下载的地址(一般先压缩一下,尽量不要用中文命名)">下载文件</a>``

使用a标签下载图片``<a href="url" download>下载图片</a>``如何不使用download会默认打开图片；或者使用js实现图片下载

```
<scipt>
	obj.onclick = function(){
        const link = document.createElement("a");
        link.href = url;
        link.download = "文件.txt";
        link.click();
	}
</script>
```

