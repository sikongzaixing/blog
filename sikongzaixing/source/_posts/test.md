---
title: Hexo 加入图片无法显示--解决方案
date: 2019-06-03 19:29:13
tags: Hexo
categories: Hexo
---

测试实例:

![image](test.png)

##### 插件安装与配置,

首先我们需要安装一个图片路径转换的插件，这个插件名字是 **hexo-asset-image**

​	`sudo npm install https://github.com/CodeFalling/hexo-asset-image --save`

##### 核心部分,需要修改 index.js文件

    'use strict';
    var cheerio = require('cheerio');
    
    // http://stackoverflow.com/questions/14480345/how-to-get-the-nth-occurrence-in-a-string
    function getPosition(str, m, i) {
      return str.split(m, i).join(m).length;
    }
    
    var version = String(hexo.version).split('.');
    hexo.extend.filter.register('after_post_render', function(data){
      var config = hexo.config;
      if(config.post_asset_folder){
        var link = data.permalink;
      if(version.length > 0 && Number(version[0]) == 3)
         var beginPos = getPosition(link, '/', 1) + 1;
      else
        var beginPos = getPosition(link, '/', 3) + 1;
        // In hexo 3.1.1, the permalink of "about" page is like ".../about/index.html".
          var endPos = link.lastIndexOf('/') + 1;
    
        link = link.substring(beginPos, endPos) ;
        var toprocess = ['excerpt', 'more', 'content'];
        for(var i = 0; i < toprocess.length; i++){
          var key = toprocess[i];
    
          var $ = cheerio.load(data[key], {
            ignoreWhitespace: false,
            xmlMode: false,
            lowerCaseTags: false,
            decodeEntities: false
          });
    
          $('img').each(function(){
            if ($(this).attr('src')){
              // For windows style path, we replace '\' to '/'.
              var src = $(this).attr('src').replace('\\', '/');
              if(!/http[s]*.*|\/\/.*/.test(src) && !/^\s*\//.test(src)) {
                // For "about" page, the first part of "src" can't be removed.
                // In addition, to support multi-level local directory.
                var linkArray = link.split('/').filter(function(elem){
                  return elem != '';
                });
                var srcArray = src.split('/').filter(function(elem){
                  return elem != '' && elem != '.';
                });
                if(srcArray.length > 1)
                srcArray.shift();
                src = srcArray.join('/');
                $(this).attr('src', config.root + link + src);
                console.info&&console.info("update link as:-->"+config.root + link + src);
              }
            }else{
              console.info&&console.info("no src attr, skipped...");
              console.info&&console.info($(this));
            }
          });
          data[key] = $.html();
        }
      }
    });

##### 打开_config.yml文件，修改下述内容

​	`post_asset_folder: true`
​	`url: http://localhost:4000/`修改为对应的地址

<font size='5' color='red'>此文使用: Typora 编写</font>