# -
微信小程序下使用absolute居中定位时出现的问题

使用微信开发者工具开发微信小程序
分别用before和after伪类来作为加号（+）的横和竖，发现横和竖不管怎么调整都有点偏离原本应该居中的位置。
.add-btn{
    width: 40rpx;
    height: 40rpx;
    background: linear-gradient(90deg, #E84369 0%, #DF2757 100%);
    border-radius: 999rpx;
    position: relative;
    text-align: center;
    color: #fff;
}
.add-btn::before{
    display: block;
    content: '';
    background: #fff;
    height: 26rpx;
    width: 4rpx;
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate3d(-50%,-50%,0);
}
.add-btn::after{
    display: block;
    content: '';
    background: #fff;
    height: 4rpx;
    width: 26rpx;
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate3d(-50%,-50%,0);
}


![BIYRMJ`GU0K{JW{`HZ{6H4I](https://user-images.githubusercontent.com/45165928/128159057-a05b03b7-806a-477d-bae3-166b1de1cefd.png)

试了很多种方法（手动调整top，left,translateX,translateY等）都没什么效果
最后发现是padding的问题（虽然我上面的代码没有设置padding）
当我把与add-btn相关的元素节点（不论是父级、子级、同级、父父级、子子级元素都是）的padding全部转换成margin或者width/height时，显示就正常了。

![EMIAD43VN~1$8PN(6LGN5CS](https://user-images.githubusercontent.com/45165928/128160005-12d6365b-e95c-42c2-bfd9-b5912e927ebb.png)

虽然不太懂原理（为什么会这样），但猜测可能是微信小程序width/height/margin/top等对rpx的适应比例和padding对rpx的适应比例不同？

