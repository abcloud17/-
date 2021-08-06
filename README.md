# 微信小程序下使用absolute定位时出现的偏移和宽高问题
微信小程序下使用absolute定位时出现的偏移和宽高问题<br>
<br>
使用微信开发者工具开发微信小程序<br>
分别用before和after伪类来作为加号（+）的横和竖，发现横和竖不管怎么调整都有点偏离原本应该居中的位置。<br>
.add-btn{<br>
    width: 40rpx;<br>
    height: 40rpx;<br>
    background: linear-gradient(90deg, #E84369 0%, #DF2757 100%);<br>
    border-radius: 999rpx;<br>
    position: relative;<br>
    text-align: center;<br>
    color: #fff;<br>
}<br>
.add-btn::before{<br>
    display: block;<br>
    content: '';<br>
    background: #fff;<br>
    height: 26rpx;<br>
    width: 4rpx;<br>
    position: absolute;<br>
    top: 50%;<br>
    left: 50%;<br>
    transform: translate3d(-50%,-50%,0);<br>
}<br>
.add-btn::after{<br>
    display: block;<br>
    content: '';<br>
    background: #fff;<br>
    height: 4rpx;<br>
    width: 26rpx;<br>
    position: absolute;<br>
    top: 50%;<br>
    left: 50%;<br>
    transform: translate3d(-50%,-50%,0);<br>
}<br>
<br>
<br>
![BIYRMJ`GU0K{JW{`HZ{6H4I](https://user-images.githubusercontent.com/45165928/128159057-a05b03b7-806a-477d-bae3-166b1de1cefd.png)<br>
<br>
试了很多种方法（手动调整top，left,translateX,translateY等）都没什么效果<br>
最后发现是padding的问题（虽然我上面的代码没有设置padding）<br>
当我把与add-btn相关的元素节点（不论是父级、子级、同级、父父级、子子级元素都是）的padding全部转换成margin或者width/height时，显示就正常了。<br>
<br>
![EMIAD43VN~1$8PN(6LGN5CS](https://user-images.githubusercontent.com/45165928/128160005-12d6365b-e95c-42c2-bfd9-b5912e927ebb.png)<br>
<br>
虽然不太懂原理（为什么会这样），但猜测可能是微信小程序width/height/margin/top等对rpx的适应比例和padding对rpx的适应比例不同？<br>

