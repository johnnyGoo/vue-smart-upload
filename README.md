# vue-smart-upload
##### upload componnent based on http://vanthink-ued.github.io/vue-core-image-upload/
### Usage
```
npm install vue-smart-upload --save
import VueSmartUpload from 'vue-smart-upload'
```
```
npm run dev
npm run build
```


### Props:
```
url	String	'/crop.php'	服务端上传的地址
text	String	'Upload Image'	你需要显示按钮的文本
inputOfFile	String    	  'file'	上传服务端对应表单 name
extensions	String	'png,jpg,gif'	限制的图片类型
crop	Mixed	false/true/'local'	是否需要裁剪 local为本地前端裁切
cropRatio	String	'1:1'	限制裁剪的形状(设置为auto表示不限制裁剪框形状)
cropBtn	Object	{ok:'Save','cancel':'Give Up'}	按钮文本
maxFileSize	Number	10485760(10M)	文件大小限制
maxWidth	Number	150	限制图片的最大宽度
maxheight	Number	150	限制图片的最大高度
inputAccept	string	'image/*' / 'image/jpg,image/jpeg,image/png'	赋予上传file的接受类型
compress	Number	50	设置本地图片压缩的质量
isXhr	Boolean	true	是否需要调用系统内自己的上传功能
headers	Object	{auth: xxxxx}	设置xhr上传 的header
data	Object	{auth: xxxxx}	设置附带发送给服务端的数据
credentials	Boolean	false	指定 XMLHttpRequest widthCredentials 的值，用于跨域的参数

:multiple="true"
:multiple-size="4"

url
url 表示我们指定的服务端配置接口地址，插件会将文件使用 Ajax 的形式上传到到你指定的地址服务，然后你可以通过imageuploaded的回调取得服务器的响应的数据。

inputOfFile
如果你的服务端端需要指定上传表单file name 的字段，你可以通过inputOfFile设置,只能是字符串如果没有设置，默认发给服务端的字段是files。如果你是使用多图片上传的话，字段会变成files[]。

extensions
限制图片的上传类型，你可以传递一组CSV数据进去比如 'png,jpg,gif'，从而只允许png,jpg,gif的类型图片上传到服务器。

maxFileSize
虽然很多时候服务端限制了图片的大小，但是本地同样可以限制上传图片的大小，你可以设置 maxFileSize的值来实现，它的基本单位为字节比如(10485760B = 10M)。

inputAccept
赋予上传file的接受类型,它可以帮助你再上传图片选择时，禁用掉不需要的文件，默认值为 image/jpg,image/jpeg,image/png

isXhr
我们同样接受取消掉默认的上传，你可以设置isXhr为 false ,自行处理我们获取到文件对象

multiple
你可以使用 multiple 属性设置为true来实现多文件的上传。需要注意的是，你设置了该属性后,服务端收到文件上传的字段数据会是一个数组。

multiple-size
你可以使用multiple-size来限制图片的数量，你可以限制上传文件的数量。

```
### Methods
```
getFileBase64(callback:Function) 获取选择图片的base64代码

```
### Event
```
imageuploaded
当图片上传完，会调用该事件绑定的函数，并且用户可以获取到服务端返回的数据。

imagechanged
当input框改变选择图片时候触发，会返回input的获取的图片数据

imageuploading
当图片上传过程中触发，你可以自定义你需要处理的内容比如显示加载动画等。

errorhandle
当图片上传发生错误的时候触发，会返回错误状态信息
```

### ServerSide
```php
      if(isset($_SERVER["HTTP_ORIGIN"])) {
            header('Access-Control-Allow-Origin:'.$_SERVER["HTTP_ORIGIN"]);
        }
        header('Access-Control-Allow-Methods: GET, POST, PUT, DELETE,OPTIONS');
        header("Access-Control-Allow-Headers: X-Requested-With, Content-Type, Accept");
        header('Access-Control-Allow-Credentials:true');

```

