# JS将图片链接直接转成base64位编码

JS将图片链接直接转成base64位编码
===
将图片链接直接转成base64位编码

```
function getBase64Image(img) {
    var canvas = document.createElement("canvas");
    canvas.width = img.width;
    canvas.height = img.height;
    var ctx = canvas.getContext("2d");
    ctx.drawImage(img, 0, 0, img.width, img.height);
    var ext = img.src.substring(img.src.lastIndexOf(".") + 1).toLowerCase();
    var dataURL = canvas.toDataURL("image/" + ext);
    return dataURL;
}
var imgLink = "你的链接";
var tempImage = new Image();
tempImage.src = imgLink;
tempImage.crossOrigin = "*";
tempImage.onload = function () {
    var base64 = getBase64Image(tempImage);
    console.log(base64);
}
```

**image.crossOrigin = "*"**是防止跨域请求时报错**Failed to execute 'toDataURL' on 'HTMLCanvasElement': Tainted canvases may n**

转载：https://blog.csdn.net/taotao12312/article/details/76209183
