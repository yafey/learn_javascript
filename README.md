# learn_javascript


#JavaScript 探查浏览器内核
>tiicle ： 记录让编码更有效：   https://tiicle.com/items/58/javascript-to-probe-the-browser-kernel  

qiezi 1 个版本 1周前

JavaScript
```
var browser = (function () {
    var u = navigator.userAgent, app = navigator.appVersion;
    return {
        trident: u.indexOf('Trident') > -1, //IE内核
        presto: u.indexOf('Presto') > -1, //opera内核
        webKit: u.indexOf('AppleWebKit') > -1, //苹果、谷歌内核
        gecko: u.indexOf('Gecko') > -1 && u.indexOf('KHTML') == -1,//火狐内核
        mobile: !!u.match(/AppleWebKit.*Mobile.*/), //是否为移动终端
        ios: !!u.match(/\(i[^;]+;( U;)? CPU.+Mac OS X/), //ios终端
        android: u.indexOf('Android') > -1 || u.indexOf('Adr') > -1, //android终端
        iPhone: u.indexOf('iPhone') > -1, //是否为iPhone或者QQHD浏览器
        iPad: u.indexOf('iPad') > -1, //是否iPad
        webApp: u.indexOf('Safari') == -1, //是否web应该程序，没有头部与底部
        weixin: u.indexOf('MicroMessenger') > -1, //是否微信 （2015-01-22新增）
        qq: u.match(/\sQQ/i) == " qq" //是否QQ
    };
}());
```
使用方法
```
if(browser.weixin) {
    // do what you want
}
```



## URL 通过 `<a>` 标签解析
https://github.com/ccforward/cc/blob/master/URLParse/index.js
```
var parser = function(url) {
    var a = document.createElement('a');
    a.href = url;

    var search = function(search) {
        if (!search) return {};

        var ret = {};
        search = search.slice(1).split('&');
        for (var i = 0, arr; i < search.length; i++) {
            arr = search[i].split('=');
            ret[arr[0]] = arr[1];
        }
        return ret;
    };

    return {
        protocol: a.protocol,
        host: a.host,
        hostname: a.hostname,
        pathname: a.pathname,
        search: search(a.search),
        hash: a.hash
    }
};

var url = 'http://sub.example.com:8088/index/?data=run&person=cc#hash';
parser(url);
```

参考以下解释：
http://w3schools.bootcss.com/jsref/dom_obj_anchor.html
https://www.xiabingbao.com/javascript/2015/11/28/js-a-parse-url.html




# TODO
SublimeText下写作利器之MarkdownEditing
http://jeffjade.com/2015/08/28/2015-08-28-Write-Morkdown/

sublime 查看 已安装插件