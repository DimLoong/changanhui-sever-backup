# 启动
cd docker
systemctl start docker


cd home/source/
sh start-api.sh
后端起的比较慢，约5分钟，ss -tulnp发现有8885-88端口即全部启动了

实时查看log
tail -f api/logs/common.out

---
## 不同端对应的端口号
ss -tulnp

8885-8891开放

common: 8890
seller: 8889
buyer: 8888
manager: 8887
im: 8885


PS：手机验证码为 ‘111111’

平台管理端
账号：adminm
密码：123456

店铺管理端
账号：13011111111
密码：111111

---




## 关闭演示禁止使用
seller/manager/buyer
api/src/main/resources/application.yml

    lili:
        system:
            isDemoSite: false

验证例如 http:公网ip:8888/actuator/env
---


## 文件修改
【修改文件】
- FileController.java
- FileDirectoryController.java

【修改内容】
- 为解决前端 localhost 调试时的 CORS 问题，添加 @CrossOrigin 注解：
  @CrossOrigin(origins = "http://localhost:10002", allowCredentials = "true")

【目的】
- 允许来自前端本地调试地址的跨域请求，避免浏览器拦截。
