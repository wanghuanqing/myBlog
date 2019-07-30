笔记
===
[TOC]
### 保留几位小数

    var money=0.00542;
    alert(Number(money).toFixed(2));
    0.01

### 字符串截取

    var money=0.00542;
    alert(Number(money).substring(0,3));
    0.0

### 字符串分割成数组

    var a="1/1/2/3/4/5/6/";
    a.split("/");
    [1,1,2,3,4,5,6]

### 数组转换字符串

    var a=[1,1,2,3,4,5,6];
    a.join("/");
    "1/1/2/3/4/5/6/"
    a.join("");
    "1123456"

### 更多隐藏

    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;

### 网易CSS初始化

    html {overflow-y:scroll;}
    body {margin:0; padding:29px00; font:12px"\5B8B\4F53",sans-serif;background:#ffffff;}
    div,dl,dt,dd,ul,ol,li,h1,h2,h3,h4,h5,h6,pre,form,fieldset,input,textarea,blockquote,p{padding:0; margin:0;}
    table,td,tr,th{font-size:12px;}
    li{list-style-type:none;}
    img{vertical-align:top;border:0;}
    ol,ul {list-style:none;}
    h1,h2,h3,h4,h5,h6{font-size:12px; font-weight:normal;}
    address,cite,code,em,th {font-weight:normal; font-style:normal;}

### 选择框设置默认值（jQuery）

    <select name="chose" id="chose">
    <option value="one"elected="selected">我是1</option>
    <option value="two">我是2</option>
    </select>
    this.$html.find(".zjmz-addChatList-limit option[value='我是2']").attr("selected",true);


### 复制到剪切板

    function copy() {
    安卓
    var getURL = plus.webview.currentWebview().getURL();
    var context = plus.android.importClass("android.content.Context");
    var main = plus.android.runtimeMainActivity();
    var clip = main.getSystemService(context.CLIPBOARD_SERVICE);
    plus.android.invoke(clip, "setText", "http://www.ihomek.com/");
    mui.toast("已成功复制链接");
    }


### 数组去重

    function uniq(array){
    var temp = []; //一个新的临时数组
    for(var i = 0; i < array.length; i++){
    if(temp.indexOf(array[i]) == -1){
    temp.push(array[i]);
    }
    }
    return temp;
    }


### 获取url中的参数

    function getUrlParam(name) {
    var reg = new RegExp("(^|&)" +
    name + "=([^&]*)(&|$)");
    var r = window.location.search.substr(1).match(reg);
    if (r != null) return decodeURI(r[2]);
    return null;
    }

-------------------------------日期格式化-----------------------------
### 年-月-日

    function Format(fmt) { //author: meizz 
    var date = new Date(fmt);
    var y = date.getFullYear(); //年 
    var m = date.getMonth() + 1; //月份
    var d = date.getDate(); //日 

    m = m >= 10 ? m : '0' + m;
    d = d >= 10 ? d : '0' + d;

    return y + '-' + m + '-' + d;
    }

### 年、月

    function Format1(fmt) { //author: meizz 
    var date = new Date(fmt);
    var y = date.getFullYear(); //年 
    var m = date.getMonth() + 1; //月份

    return y + '年' + m + '月';
    }

### 年/月/日/时/分/秒

    function Format2(fmt) { //author: meizz
    var date = new Date(fmt);
    var y = date.getFullYear(); //年
    var m = date.getMonth() + 1; //月份
    var d = date.getDate(); //日
    var h = date.getHours(); //日
    var mi = date.getMinutes(); //日
    var s = date.getSeconds(); //日

    m = m >= 10 ? m : '0' + m;
    d = d >= 10 ? d : '0' + d;
    h = h >= 10 ? h : '0' + h;
    mi = mi >= 10 ? mi : '0' + mi;
    s = s >= 10 ? s : '0' + s;

    return y + '-' + m + '-' + d + " " + h + ":" + mi + ":" + s;
    }

### 年/月/日

    function Format3(fmt) { //author: meizz
    var date = new Date(fmt);
    var y = date.getFullYear(); //年
    var m = date.getMonth() + 1; //月份
    var d = date.getDate(); //日
    <!-- var h = date.getHours(); 日
    var mi = date.getMinutes(); 日
    var s = date.getSeconds(); 日 -->

    m = m >= 10 ? m : '0' + m;
    d = d >= 10 ? d : '0' + d;
    <!-- h = h >= 10 ? h : '0' + h;
    mi = mi >= 10 ? mi : '0' + mi;
    s = s >= 10 ? s : '0' + s; -->

    <!-- return y + '-' + m + '-' + d + " " + h + ":" + mi + ":" + s; -->
    return y + '-' + m + '-' + d

    }


### 调用本地返回键>

    document.addEventListener("plusready", function () {

    var first = null;
    plus.key.addEventListener('backbutton', function () {

    if (!first) {
    first = new Date().getTime();
    plus.nativeUI.toast('再按一次退出应用');
    setTimeout(function () {
    first = null;
    }, 1500);
    } else {
    if (new Date().getTime() - first < 1500) {

    plus.runtime.quit();
    }
    }
    }, false);
    });

### 监听断网

    var EventUtil = {
    addHandler: function (element, type, handler) {
    if (element.addEventListener) {
    element.addEventListener(type, handler, false);
    } else if (element.attachEvent) {
    element.attachEvent("on" + type, handler);
    } else {
    element["on" + type] = handler;
    }
    }
    };

    EventUtil.addHandler(window, "online", function () {
    console.log("连网了");
    window.location.reload();
    });

    EventUtil.addHandler(window, "offline", function () {
    console.log("断网了");
    openchangePrompt("3");
    });

### 判断是否连网

    if(window.navigator.onLine==true) {
    console.log("已连网");
    }else {
    console.log("未连网");
    }


### 点击眼睛查看密码

    <span class="openEye changeEye"></span>
    .openEye{
        background: url(../../img/secondHouse_img/openEye.png) no-repeat;
        background-size: 100%;
    }
    .closeEye{
        background: url(../../img/secondHouse_img/closeEye.png) no-repeat;
        background-size: 100%;
    }
    $(".userinfo_main_csrq i").click(function(){

        if ($( this ).siblings("input").attr("type") == "text") {
            $( this ).siblings("input")[0].type = "password";  
            $( this ).removeClass("userinfo_main_csrq_i");   
        }else{
            $( this ).siblings("input")[0].type = "text"; 
            $( this ).addClass("userinfo_main_csrq_i");   
        }   
    });

### 页面跳转前执行AJAX

    window.onbeforeunload() 事件调用ajax的解决方法

    function window.onbeforeunload() {

        var jhid = $("#ctl00_ContentBody_hfGuid").val();
        $.ajax({
            url: "AjaxServices/AjaxService.asmx/DeleteDeviceAndWorkContent", // ajax 调用后台方法
            type: "POST",
            async: false,
            data: "{'jhid':'" + jhid + "'}", // 参数
            dataType: "json", // 返回类型
            contentType: "application/json; charset=utf-8",
            //成功时调用的方法
            success: function(data) {
            },
            error: function(XMLHttpRequest, textStatus, errorThrown) {
                alert(XMLHttpRequest);
                alert(textStatus);
                alert(errorThrown);
            }
        });
        
    }

