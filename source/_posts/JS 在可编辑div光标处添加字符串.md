---
title: JS 在可编辑div光标处添加字符串
categories:
  - 前端
date: 2018-02-24 14:37:24
tags:
  - JavaScript
---

JS 在可编辑div光标处添加字符串,应该也可以在textarea中使用, 没有测试. 在div中亲测可用,

**editContent 是div标签**

    function insertStr(str){
      var selection= window.getSelection ? window.getSelection() : document.selection;
      var range= selection.createRange ? selection.createRange() : selection.getRangeAt(0);
      if (!window.getSelection){
        document.getElementById('editContent').focus();
        var selection= window.getSelection ? window.getSelection() : document.selection;
        var range= selection.createRange ? selection.createRange() : selection.getRangeAt(0);
        range.pasteHTML(str);
        range.collapse(false);
        range.select();
      }
      else{
        document.getElementById('editContent').focus();
        range.collapse(false);
        var hasR = range.createContextualFragment(str);
        var hasR_lastChild = hasR.lastChild;
        while (hasR_lastChild &amp;&amp; hasR_lastChild.nodeName.toLowerCase() == "br" &amp;&amp; hasR_lastChild.previousSibling &amp;&amp; hasR_lastChild.previousSibling.nodeName.toLowerCase() == "br") {
          var e = hasR_lastChild;
          hasR_lastChild = hasR_lastChild.previousSibling;
          hasR.removeChild(e)
        }
        range.insertNode(hasR);
        if (hasR_lastChild) {
          range.setEndAfter(hasR_lastChild);
          range.setStartAfter(hasR_lastChild)
        }
        selection.removeAllRanges();
        selection.addRange(range)
      }
    }