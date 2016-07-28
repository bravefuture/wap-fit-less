# Wap 自适应开发 
## 设置html fontSize (以下“640”为设计稿宽度)
```html
<script>
    !function(n,e){var t=e.documentElement,i='orientationchange'in n?'orientationchange':'resize',d=function(){var n=t.clientWidth
        n&&(t.style.fontSize=100*(n/640)+'px')}
        e.addEventListener&&(n.addEventListener(i,d,!1),e.addEventListener('DOMContentLoaded',d,!1),d())}(window,document)
</script>
```

## LESS 代码
```less
/**
 * mixin
 */

/**
 * 单行垂直居中
 */
.l-h(@h){ height: @h; line-height: @h; }

/**
 * 单行溢出生成省略号
 */
.ellipsis(){ overflow: hidden; text-overflow: ellipsis; white-space: nowrap; word-break: normal; }

/**
 * 间隔
 */
.blank(@h){ height: @h; display: block; overflow: hidden; clear: both; }

/**
 * 垂直居中
 */
.vertical(){ display: table-cell; vertical-align: middle; }

/**
 * 圆角
 */
.radius(@r){ border-radius: @r; }

/**
 * 文字阴影
 */
.text-shadow(@x, @y, @blur, @color){ text-shadow: @arguments; }

/**
 * 图层阴影
 */
.box-shadow(@x, @y, @blur, @color){ 
	-webkit-box-shadow: @arguments; 
	-moz-box-shadow: @arguments; 
	box-shadow: @arguments; 
}

/**
 * 垂直渐变
 */
.v-g(@s-c, @e-c, @d-c){ 
	background-color: @d-c; 
	background: -webkit-gradient(linear, left top, left bottom, from(@s-c), to(@e-c)); 
	background: -webkit-linear-gradient(top, @s-c, @e-c); 
	background: -moz-linear-gradient(top, @s-c, @e-c);
	background: -o-linear-gradient(top, @s-c, @e-c); }

/**
 * 水平渐变
 */
.h-g(@s-c, @e-c, @d-c){
 	background-color: @d-c;
	background-image: -webkit-gradient(linear, left top, right top, from(@s-c), to(@e-c));
	background-image: -webkit-linear-gradient(left, @s-c, @e-c);
	background-image: -moz-linear-gradient(left, @s-c, @e-c);
	background-image: -o-linear-gradient(left, @s-c, @e-c);
}

/**
 * 过渡效果
 * .target{ width: 100px; .transition(); }
 * .target:hover{ width: 300px; }
 */
.transition(@property: all; @duration: 600ms; @function: linear; @delay: 0ms){
	transition: @arguments;
	-webkit-transition: @arguments;
	-moz-transition: @arguments;
	-ms-transition: @arguments;
	-o-transition: @arguments;
}

/**
 * 动画
 * linear: 规定以相同速度开始至结束的过渡效果。
 * ease: 规定慢速开始，然后变快，然后慢速结束的过渡效果。
 * ease-in: 规定以慢速开始的过渡效果。
 * ease-out: 规定以慢速结束的过渡效果。
 * ease-in-out: 规定以慢速开始和结束的过渡效果。
 * cubic-bezier(n,n,n,n): 在 cubic-bezier 函数中定义自己的值。可能的值是 0 至 1 之间的数值。
 例子：
@keyframes bounceIn{
	0%{ opacity: 0; transform: scale(.3); }
	100%{ opacity: 1; transform: scale(1); }
}
@-webkit-keyframes bounceIn{
	0%{ opacity: 0; -webkit-transform: scale(.3); }
	100%{ opacity: 1; -webkit-transform: scale(1); }
}
@-moz-keyframes bounceIn{
	0%{ opacity: 0; -moz-transform: scale(.3); }
	100%{ opacity: 1; -moz-transform: scale(1); }
}
@-o-keyframes bounceIn{
	0%{ opacity: 0; -o-transform: scale(.3); }
	100%{ opacity: 1; -o-transform: scale(1); }
}
.mod{
    .animation(bounceIn; 600ms; linear);
}
 */
.animation(@name; @duration: 600ms; @ease: linear; @times: 1){
    animation: @arguments;
    -webkit-animation: @arguments;
    -moz-animation: @arguments;
    -ms-animation: @arguments;
    -o-animation: @arguments;
}

/**
 * 旋转
 */
.rotate(@deg){
	transform: rotate(@deg);
	-webkit-transform: rotate(@deg);
	-moz-transform: rotate(@deg);
	-ms-transform: rotate(@deg);
	-o-transform: rotate(@deg);
}

/**
 * 位移
 */
.translate(@x, @y){
    transform: translate(@x, @y);
	-webkit-transform: translate(@x, @y);
	-moz-transform: translate(@x, @y);
	-ms-transform: translate(@x, @y);
	-o-transform: translate(@x, @y);
}

/**
 * 倾斜
 */
.skew(@deg-x, @deg-y) {
    transform: skew(@deg-x, @deg-y);
    -webkit-transform: skew(@deg-x, @deg-y);
    -moz-transform: skew(@deg-x, @deg-y);
    -ms-transform: skew(@deg-x, @deg-y);
    -o-transform: skew(@deg-x, @deg-y);
}

/**
 * 旋转、缩放、移动或倾斜
 */
.transform(@args){
    transform: @args;
	-webkit-transform: @args;
	-moz-transform: @args;
	-ms-transform: @args;
	-o-transform: @args;
}

/**
 * 以320px分辨率为基准
 * 页面宽度为3.2rem;(js会计算不同分辨率下html的fontSize，在fontSize为100px时页面宽度定为3.2rem)
 * 640px设计稿的1px等于3.2/640=0.005rem;
 */
@base-rem: 0.005rem;
.w-rem(@w){ width: @base-rem*@w;}
.h-rem(@h){ height: @base-rem*@h; }
.f-rem(@f){ font-size: @base-rem*@f; }
.m-rem(@t, @r, @b, @l){ margin: @t*@base-rem @r*@base-rem @b*@base-rem @l*@base-rem; }
.ml-rem(@l){ margin-left: @l*@base-rem; }
.mt-rem(@t){ margin-top: @t*@base-rem; }
.mr-rem(@r){ margin-right: @r*@base-rem; }
.mb-rem(@b){ margin-bottom: @b*@base-rem; }
.ma-rem(@t, @b){ margin: @base-rem*@t auto @base-rem*@b; }
.p-rem(@t, @r, @b, @l){ padding: @t*@base-rem @r*@base-rem @b*@base-rem @l*@base-rem; }
.pl-rem(@l){ padding-left: @l*@base-rem; }
.pt-rem(@t){ padding-top: @t*@base-rem; }
.pr-rem(@r){ padding-right: @r*@base-rem; }
.pb-rem(@b){ padding-bottom: @b*@base-rem; }
.lh-rem(@l-h){ line-height: @l-h*@base-rem; }
.l-rem(@l){ left: @base-rem*@l; }
.t-rem(@t){ top: @base-rem*@t; }
.r-rem(@r){ right: @base-rem*@r; }
.b-rem(@b){ bottom: @base-rem*@b; }
.ti-rem(@t-i){ text-indent: @base-rem*@t-i; }
.va-rem(@v-a){ vertical-align: @base-rem*@v-a; }

/**
 * 合并图定位
*/
.bg-p-s(@bg-w, @bg-h, @w, @h, @x, @y){ @x-dis: @bg-w - @w; @y-dis: @bg-h - @h; background-position: @x/@x-dis*100% @y/@y-dis*100%; background-size: @bg-w/@w*100%; }
```
