---
title: JS 禁用按键
tags:
  - JavaScript
categories:
  - 前端
date: 2018-02-24 14:25:03
---

**禁用组合按键 ctrl + s**

    document.onkeydown = function (e) {
        e = e || window.event;//Get event
        if (e.ctrlKey) {
            var c = e.which || e.keyCode;//Get key code
            switch (c) {
                case 83://Block Ctrl+S
                    e.preventDefault();     
                    e.stopPropagation();
                break;
            }
        }
    };
    

**禁用单个键 tab**

        function HandleTabKey(evt) {
            if (evt.keyCode == 9) {
                 if (evt.preventDefault) { evt.preventDefault(); }
                else { evt.returnValue = false; }
            }
        }