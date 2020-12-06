# 学习笔记

## Proxy, reactive, 双向绑定

1. 实现通过range双向绑定，调整数据

## Dragable

1. 实现拖拽，对range的操作有了进一步了解。

## 参考笔记，根据讨论区而来

1. Range 经常配合 selection 被用来操作文字范围做划词插件和编辑器。

1. document.addEventListener('mouseup', () => { 

1. var html = '',selection = document.getSelection();

1. if(selection.rangeCount > 0) {

1. for(var i = 0; i < selection.rangeCount; i++) {

1. var range = selection.getRangeAt(i);

1. html += `${i+1}:${range};`;

1. }

1. }

1. })

1. 又比如测量一个文字节点的高度。

1. const range = document.createRange();

1. range.selectNodeContents(textNode);

1. const rect = range.getBoundingClientRect();

1. console.log(rect.bottom - rect.top);

1. 有个细节。当move事件挂载在drag节点上，拖动过快时容易脱离挂掉。应该挂载在document上。

1.  <script>
let dy = 0, dx = 0;
const dragable = document.getElementById('drag');

const mousedown = (evt) => {
const startX = evt.pageX - dx;
const startY = evt.pageY - dy;

const move = e => {
dx = e.pageX - startX;
dy = e.pageY - startY;
dragable.style.transform = `translate3d(${dx}px, ${dy}px, 0)`;
}

document.addEventListener('mousemove', move);
document.addEventListener('mouseup', () => {
document.removeEventListener('mousemove', move);
}, { once: true });
}

dragable.addEventListener('mousedown', mousedown)
</script>