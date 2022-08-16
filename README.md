# 自考登录油猴脚本
四川省考试院自考报名登录油猴脚本

https://zk.sceea.cn

## 
下面是脚本
```js
// ==UserScript==
// @name         自动登录
// @namespace    http://tampermonkey.net/
// @version      0.1
// @description  try to take over the world!
// @author       Ray
// @match        https://zk.sceea.cn*
// @grant        *
// ==/UserScript==

(function() {
    alert("填号账号密码验证码后点击登录后脚本将会自动登录, 直至登录成功！")

    // Your code here...
    var failCount=0;var yzm="1";
    var login = unsafeWindow.login.toString();
    login = login.replace(/alert/g, "console.log");
    login = login + ";login();showCount()";
    console.log("开始启动了");
    var fnLogin = new Function(login);

    $("#btn_login")[0].onclick = null;
    $("#btn_login").click(function() {
        fnLogin();
        setTimeout(arguments.callee, 3000);
    })

    unsafeWindow.count = 0;
    unsafeWindow. showCount = function() {
        unsafeWindow.count ++;
     var msg = "正在尝试第" + unsafeWindow.count + "次登录";
        $("#errorMsg").html(msg)
    }


})();
```
