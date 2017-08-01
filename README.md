# 原生js手势截图功能

## 用法
1.  页面引入,可直接引用
```

1. 直接引用<script src="../mobileCliImg.js"></script>
2. var ClipImg = require('mobileCliImg');
3. import ClipImg from 'mobileCliImg';
```
2.  具体用法
```js 
new ClipImg({
            fileId: 'test',       //
            width: 600,          // 截取图的长
            height: 600,         // 截取图的高
            showId: 'showImag',  // 预览图的id
            format: 'png,jpg,jpeg', // 格式限定
            targetDensitydpi: 1, //缩放比例,如果用rem布局，需计算出缩放比列
            dealFun: function (res) {          //上传内置方法
                switch (res.status) {
                    case 0 ://读取图片中..增加loading状态
                        console.log('0 正在读取图片...');
                        alert('0 正在读取图片...');
                        break;
                    case 1 ://读取结束..取消loading状态
                        console.log('1 读取图片结束...');
                        alert('1 读取图片结束...');
                        break;
                    case 2 ://截图成功
                        console.log('2 截图图片结束...');
                        alert('2 截图图片结束...');
                        console.log(res.blob);        //截图成功后的blob格式图片，可直接ajax上传
                        console.log(res.base64);      //截图成功后的base64格式图片，可预览
                        break;
                    case 3 ://不符合格式，有format时才会执行
                        console.log('3 格式错误，请上传格式的照片');
                        alert('3 格式错误，请上传格式的照片');
                        break;
                    case 5 : //图片不够限定的长宽
                        console.log('4 尺寸不足600*600哦');
                        alert('5 尺寸不足600*600哦');
                        break;
                    case 6 : //图片截图呈现异常
                        console.log('6 图片损害，请替换一张图片');
                        alert('6 图片损害，请替换一张图片');
                        break;
                }
            }
        })

```