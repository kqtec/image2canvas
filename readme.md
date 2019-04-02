#### image2Canvas

通过canvas将图片资源和文字合成在一张图片上

### install
        npm install image2Canvas --save

### Usage

        const image2Canvas =require("image2canvas") ;

        image2Canvas(base,image,text,cb);

        
### 参数详解：

| 名称 | 是否可选 | 类型 | 解释 |
| ------| ------| ------| ----- |
| base | 是 | Object | 合成图片的底图 |
| image | 否 | Array | 需要合成的图片,其数组元素为对象 |
| text | 否 | Array | 需要合成的文字，数组元素为对象 |
| cb |  是 | Function | 合成之后的回调函数 |


#### base
| 名称 | 是否可选 | 类型 | 解释 |
| ------| ------| ------| ----- |
| url | 是 | String | 合成图片的底图,可以是地址或者图片base64数据 |
| width | 　是 | Number | 需要合成的图片宽度 |
| height | 是 | Number | 需要合成的图片高度 |


#### image中元素的属性

| 名称 | 是否可选 | 类型 | 解释 |
| ------| ------| ------| ----- |
| url | 是 | String | 需要合成的图片,可以是地址或者图片base64数据 |
| width | 　是 | Number | 需要合成的图片宽度 |
| height | 是 | Number | 需要合成的图片高度 |
| sx | 是 | Number | 图片左上角距离底图左上角的横轴距离 |
| sy | 是 | Number | 图片左上角距离底图左上角的纵轴距离 |


####  text中元素的属性
| 名称 | 是否可选 | 类型 | 解释 |
| ------| ------| ------| ----- |
| content | 是 | String | 需要合成的文字 |
| sx | 　是 | Number |文本中心相对于底图的 x坐标 |
| sy | 是 | Number | 文本中心相对于底图的y坐标 |
| color | 可选 |String | 文字颜色|
| font | 可选 | String | 文字样式。default:"24px sans-serif" |
| lineHeight | 可选 | String | 文字行高，default:30 |


#### cb

| 名称 |   类型 | 解释 |
| ------| ------| ------| ----- |
| data  | String | 合成的图片base64数据 |


###example
    var base = "./img/img-poster@2x.png";
    var compose = "./img/img-wenbenkuang@2x.png";
    var qrCode = "./img/img-QRcode@2x.png";

    image2canvas({
        url:base,
        width:750,
        height:1206,
    },[{
        url:compose,
        width:605,
        height:636,
        sx:72,
        sy:84,
    },{
        url:qrCode,
        width:115,
        height:115,
        sx:322,
        sy:520,
    }],[
        {
            content:'xxx&&在意大利的朱丽叶故居，用意大利语许下&&了2019年的第一个关于XX的愿望。',
            sx:375,
            sy:160,
            // color:"#876746",
            // font:"30px sans-serif",
            lineHeight:"30",
        },{
            content:"Ta的愿望守护咒语是&&'L'Amore di dio con te'",
            sx:375,
            sy:382,
            // color:"#876746",
            // font:"30px sans-serif",
            lineHeight:"30",

        }
    ],function(data){
        var imgContainer = document.getElementById('img-container');
        imgContainer.src = data;
    })