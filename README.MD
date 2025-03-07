# uniapp小程混入到微信原生小程序

场景：用uniapp实现的小程序中，一部分页面与逻辑要复用在另一个用原生语法的小程序中；或者部分新功能想用uniapp来实现。

操作步骤：

1.  创建原生小程序简易demo
2.  创建uniapp简易demo
3.  使用uniapp发行为混合分包的功能（[uniappp官网教程](https://uniapp.dcloud.net.cn/hybrid.html)）
4.  将打包好的文件夹迁移到原生小程序中
5.  在原生小程序app.json中配置分包

    ```json
    "subPackages": [
        {
          "root": "subpackage",
          "name": "subpackage",
          "pages": [
            "pages/test/test"
          ]
        }
      ],
    ```


6.  验证，在原生小程序中跳转到分包页面查看是否生效

    遇到报错 `Framework inner error (expect FLOW\_INITIAL\_CREATION end but get FLOW\_CREATE\_NODE)`

    处理方法：去除app.json中的 `"lazyCodeLoading": "requiredComponents"` 配置

    [关于lazyCodeLoading](https://developers.weixin.qq.com/miniprogram/dev/framework/ability/lazyload.html)
7.  成功跳转到uniapp混入的分包页面

[demo仓库](https://github.com/fangcuidong/wxmp_uniapp_minix/)
