# MyTooL-1
## MyTool工具 - 专门来解决DOM操作中的问题及浏览器兼容性 - Node对象中获取子节点和兄弟节点时的空白节点问题 
```js
/*
    firstChild()函数 - 用于解决获取第一个子节点的空白节点
    * 参数
      * parentNode - 表示调用firstChild属性时的父级节点
 */
function firstChild(parentNode){
    // 1.正确的子节点；2.空白节点
    var child = parentNode.firstChild;
    // 判断当前是否为空白节点
    if (child.nodeType === 3){
        child = child.nextSibling;
    }
    return child;
}
function childNodes(parentNode){ // 获取所有的子节点
    var arr = []; // 定义一个空数组来存储数据
    var children = parentNode.childNodes; //定义一个局部变量为所有的子节点的集合
    for(var i=0;i<children.length;i++){ //先遍历所有的子节点
        var child = children[i]; // 定义一个变量为每一个子节点
        if(child.nodeType === 1){
            arr.push(child); // 一个条件判断，若是为子节点则用push方法将值追加到数组中并返回数组的新长度。
        }
    }
    return arr;
}
function lastChild(parentNode){
    var child = parentNode.lastChild;// 定义一个局部变量为父节点的最后一个子节点
    if(child.nodeType === 3){
        child = child.previousSibling;// 条件判断若是为文本节点，变量则为其前面一个兄弟节点
    }
    return child;
}
function previousSibling(node){
    var prev = node.previousSibling;// 定义局部变量为某前面一个兄弟节点
    if (prev.nodeType === 3){
        prev = prev.previousSibling;// 条件判断若是文本节点则为其前面的一个兄弟节点
    }
    return prev;
}
function nextSibling(node){
    var next = node.nextSibling;// 定义局部变量为某后面一个兄弟节点
    if(next.nodeType === 3){
        next = next.nextSibling;// 条件判断若是文本节点则为其后面的一个兄弟节点
    }
    return next;
}
```
