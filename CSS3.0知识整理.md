#CSS3--知识整合
##一、CSS
	1. css（cascading style sheet）层叠样式表
	2. css的组成：
		样式表
		  *规则
			*选择器+声明块
				*声明
					*css属性名+css属性值组成的键值对
	3. 浏览器对css选择器的渲染顺序：从右往左.特点：性能高，算法难度低
	4. CSS3选择器规范地址：	   https://www.w3.org/TR/2011/REC-css3-selectors-20110929/                    n 
	   CSS3选择最新选择器规范:  https://www.w3.org/TR/selectors 
##二、CSS3.0（level3）
## 1.选择器
----------
	 1.1 基本选择器
----------
		* ID选择器 -- `#`
		* 类选择器 -- `.`
		* 通配符选择器 -- `*`
		* 后代选择器 -- `空格`
		* 元素选择器 -- `ele`
		* 组合选择器 -- `直接连在一起`
	 1.2 扩展选择器 
----------
		* 子元素选择器 -- `>`
		* 相邻兄弟选择器 -- `+` -- 目标元素后的兄弟
		* 通用兄弟选择器 -- `~` -- 目标元素后的兄弟
		* 选择器分组 -- `，`-- `，`结合符 
	 1.3 属性选择器 --属性值用“”括起来
----------
		* 存在和值选择器
			* [attr] -- 选择带有attr属性的所有元素
			* [attr=“val”] -- 选择带有attr属性且值为val的所有元素
			* [attr~=“val”] -- 表示带有以 attr 命名的属性的元素，并且该属性是一个以空格作为分隔的值列表，其中至少一个值为val。
				* 属性值或者是值的前面或者后面有空格与其它字符分隔
		* 子串值属性选择器
			* [attr*=“val”] -- attr值为val的元素
			* [attr|=“val”] -- attr值为val或者是以val-开头的元素
			* [attr$=“val”] -- attr的属性值以val结尾的元素（包含val）
			* [attr^=“val”] -- attr的属性值以val开头的元素（包含val）
	 1.4 伪类与伪元素选择器
----------
		* 链接（锚点）伪类 -- 仅作用于链接元素
			* :visited -- 访问过的地址的锚
			* :link -- 未访问的地址的锚
			* :target -- 代表一个特殊的元素，它的id是URI的片段标识符
		* 动态伪类
			* ：hover --悬浮在元素上
			* ：active -- 表示匹配被用户激活的元素(点击按住时)
			* 注意：
				1.由于a标签的：link和：visitied可以覆盖a标签的状态。所以当：link，：visited，：hover，：active同时出现在a标签中的时候，：link和：visited不能放在最后。可以这样记lvhat
				2.隐私与：visited 只可以设置三个属性：color background-color boeder-color <br>
		* 表单相关伪类
			* ：enabled -- 匹配可编辑的表单
			* ：disable -- 匹配被禁用的表单
			* ：checked -- 匹配被选中的表单
			* ：focus -- 匹配获取焦点的表单
		* 结构性伪类
		  * index的值从1开始计数
			* ele:nth-child(index) --表示匹配#wrap中第index的子元素 这个子元素必须是ele
			* ele:nth-of-type(index) -- 表示匹配#wrap中第index的ele子元素
			!!!区别：nth-of-type以元素为中心！！！
			* :nth-child(index)系列			
					:first-child
					:last-child
					:nth-last-child(index)
					:only-child	(相对于:first-child:last-child 或者 :nth-child(1):nth-last-child(1))
			* :nth-of-type(index)系列
					:first-of-type
					:last-of-type
					:nth-last-type(index)
					:only-of-type	(相对于:first-of-type:last-of-type 或者 :nth-of-type(1):nth-last-of-type(1))
			# index值可以为变量n（正无穷） odd（奇数） even（偶数） 2n+1（奇数）
			* :not -- 非
			* :empty -- 内容必须是空的，有空格都不行
		* 伪元素 -content: ""; display: block;	
			* ：：after --会产生结构 不在DOM树中 
			* ：：before --会产生结构 不在DOM树中
			* ：：firstLetter -- 第一个字
			* ：：firstLine -- 第一行
			* ：：selection -- 选中的背景
			* ：：root -- 选中根目录标签
##
##2.CSS声明的优先级
	2.1. 选择器的特殊性 -- 由选择器本身的组件确定
	  2.1.1 一个选择器的具体特殊性如下
		① ID属性值 0 1 0 0
		② 类属性/属性选择器/伪类 0 0 1 0
		③ 各个元素/伪元素 0 0 0 1
		④ 通配符选择器的特殊性 0 0 0 0
		⑤ 结合符`，`对选择器没有一点贡献
		⑥ 内联声明的特殊性最强 1 0 0 0 
		⑦ 继承没有特殊性 (4>7)不如0 0 0 0
	  * 1 0 0 0 大于所以以0 开头的特殊性（不进位）
	  * 选择器的特殊性最终都会授予给其对应的声明
	  * 如果多个规则与同一个元素匹配，而且有些声明互相冲突时，特殊性越大的越占优势
	  * 注意：id选择器和属性选择器
				      div[id="test"]（0,0,1,1） 和 #test（0,1,0,0）
	2.2 重要声明
		* 在每个声明结束分号前插入！important
		* 所有的重要声明会被浏览器分为一组，重要声明的冲突会在其内部解决
		非重要声明也会被分为一组，非重要声明的冲突也会在其内部解决
		如果一个重要声明与非重要声明冲突，胜出的总是重要声明
	2.3 css样式的来源
		* 创作人员 -- 开发人员
		* 读者 --用户
		* 用户代理 -- 浏览器
	#权重
		* 读者的重要声明 （外部写css插入浏览器并且是重要声明）
			* 创作人员的重要声明
				* 创作人员的正常声明
					* 读者的正常声明
						* 用户代理的声明
	#层叠
		1.找出所有相关的规则，这些规则都包含一个选择器
		2.计算声明的优先级
		      先按来源排序
		      在按选择器的特殊性排序
		      最终按顺序
##3.css3.0
	3.1 自定义字体
		* 能让所以的客户端使用字体
		* 字体图标基本思路
		  1.设计一套矢量图（svg）
		  2.将不同的矢量图绑定到不同的字符上生成自定义字体
		  3.一般通过工具或者站点来生成一套字体
		  4.在页面中引用 
		* 引用方法
			* @font-face{font-family：‘’；src：url（）}
		* 特点
			* 摆脱用户系统的字体
			* 易于操作
			* 增加网络负担，每次打开需要加载这个字体
		* 目的 先实现需求，再优化
		* 字体兼容处理网站
	       https://www.fontsquirrel.com/tools/webfont-generator
	    * icomoon字体图标
	       https://icomoon.io/#home
	3.2 文本新增样式
		**透明度
			opacity：0~1 性能高，不是继承属性，但是可以影响后代元素
			rgba：0~1
		**文字阴影
			text-shadow：添加阴影，可叠加多层
			filter: blur(10px);
		**文字描边
			-webkit-text-stroke 
		**文字排版
			direction：ltr/rtl 必须配合unicode-bidi：bidi-override;文字从右向左
		**文字溢出显示省略号
			① white-space：nowrap
			② text-overflow：ellipsis省略号/clip隐藏
			③ overflow：hidden隐藏
			④ 包裹区域必须不能让子元素撑开
			此三条必须同时使用，并且元素必须为block/inline-block
	3.3 盒模型新增样式
		（1） 盒模型倒影 --box-shadow
		    * 默认值：none 
		    * 继承性：不继承
		    * 可设置多个阴影之间用“，”隔开
		    * box-shadow:投影方式 X轴偏移量 Y轴偏移量 阴影模糊半径 阴影扩展半径 阴影颜色；
				- 阴影类型：此参数可选。如不设值，默认投影方式是外阴影；如取其唯一值“inset”，其投影为内阴影；
				- offset-x/y:阴影水平/垂直偏移量，其值可以是正负值。如果值为正值，则阴影在对象的右/下边，其值为负值时，阴影在对象的左/上边；
				- 阴影模糊半径：此参数可选，但其值只能是为正值，如果其值为0时，表示阴影不具有模糊效果，其值越大阴影的边缘就越模糊；
				- 阴影扩展半径：此参数可选，其值可以是正负值，如果值为正，则整个阴影都延展扩大，反之值为负值时，则缩小；
				- 阴影颜色：此参数可选。如不设定颜色，浏览器会取默认色，但各浏览器默认取色不一致，特别是在webkit内核下的safari和chrome浏览器下表现为透明色，在Firefox/Opera下表现为黑色（已验证），建议不要省略此参数。
		    * -moz-box-shadow --Firefox
		    * -webkit-box-shadow -- chrome Safariand Google
		（2） 倒影 ---webkit-box-reflect
			* 不是css3的东西 -webkit内核
			* 默认值：none
			！！！属性值顺序不能改变
			* -webkit-box-reflect：方向 距离 渐变
			   - 倒影的方向--above（倒上），below（倒下），right（倒右），left（倒左）##倒影在它的什么位置
			   - 倒影的距离--倒影之间的间距 px/%
			   - 渐变 linear-gradient
		（3）resize -- 
			* 控制一个元素的可调整大小
			！！！ 一定要配合overflow：auto
			* 默认值：none
			* 不继承
			* none -- 元素不能被用户缩放。 
			* both -- 允许用户在水平和垂直方向上调整元素的大小
			* horizontal -- 允许用户在水平方向上调整元素的大小
			* vertical -- 允许用户在垂直方向上调整元素的大小
	     （4）box-sizing --
			* 不继承
			* border-box -- width/height包含内容/内边距和边框但是不包括外边距。
			-- width = 内容的宽度，
			-- height = 内容的高度
			* content-box -- 默认值width/height只包含内容的宽高。
			--width = border + padding + 内容的width，
			--height = border + padding + 内容的height
	3.4 新增UI样式
		（1）圆角 -- border-radius
			* 不继承 
			* px/%
			* 最多50%
			* 左上--右下  右上--左下
			* 顺序：左上，右上，右下，左下
		（2）边框图片 -- border-image
			* 不继承
			* border-image-source: url
			* border-image-slice: 四个切片值默认100%  fill填充中间
			* border-image-width: 边框图片的大小
			* border-image-repeat: stretch（拉伸）/round/repeat（平铺） 单个值的时候，设置所有的边框；或为两个值，分别设置水平与垂直的边框。
			* border-image-outset: none定义边框图像可超出边框盒的大小，不能为负值
		（3）背景
			* css2：
			    - bg-color：
				- bg-image：--可设置多个背景，以z轴方向排列，先写的图片会覆盖后面的图片
				- bg-repeat：
				- bg-position：控制背景图片在背景区域中的位置
					- 可% 容器大小减去图片大小/px
				- bg-attachment-fixed/scroll-fixed是为视口平铺固定在视口上（性能不好）
			* css3
				* 默认情况下背景图片是从padding-box开始绘制，从border-box开始剪裁
				- bg-origin --表示从哪绘制 padding-box/border-box/content-box
				- bg-clip -- 表示从哪开始裁剪
				 padding-box/border-box/content-box/text（-webkit中）
				- bg-size -- 图片自适应
				- bg--简写属性-如果需要写的属性多的话，尽量别选简写
		（4）渐变--background-image下使用必须
			* 线性渐变--linear-gradient
				* linear-gradient（角度，to方向，color px/%，color px/%）
				* 颜色可以叠加多个 
				* to方向可选 top/right/left/bottom
				* 角度：单位edg 
				* repeating-linear-gradient--只重复渐变的那一部分
				* rgba（0，0，0，0~1）渐变/color渐变
		     * 径向渐变 -- radial-gradient（）
			     * （cricle，color px，color px）
			     * scricle--改变渐变的形状，默认值为ellipse椭圆
			     * 默认均匀分布
				     *  radial-gradient(red,blue);
				 * 不均匀分布
					 * radial-gradient(red 50%,blue 70%);
			     * 渐变形状的大小
			     * radial-gradient(closest-corner  circle ,red,blue)
				     * closet-side 最近边
				     * farthest-side 最远边
				     * closest-corner 最近角
				     * farthest-corner 最远角  （默认值）
				 * 改变圆心
					 *  radial-gradient(closest-corner  circle at 10px 10px,red,blue);
			（5）过渡
			（6）2D变换
			1.在元素首次渲染还没有完成的情况下,是不会触发过渡的
			2.在绝大部分变换样式切换时,如果变换函数的位置 个数不相同也不会触发过渡

 
   

   
            
 


 
    