
#Android Stduio入门笔记

----------


## 线性布局

- id
- layout_width
- layout_height
- background
- layout_margin  *外边距*
- layout_padding *内边距*
- orientation *排列规则垂直or水平*

## 相对布局

- layout_toLeftOf
- layout_toRigthOf *相对位置*
- layout_alignBottom *对齐*
- layout_alignParentBottom  *和父框对齐*
- layout_below *相对位置*

## TextView

- 大小 textSize textColor
- 显示不下使用  maxLines="1" ellipsize="end"
- 文字+icon drawableRight="@.." 添加在drawable的图片名字
- 中划线，下划线 java代码中实现
 ```
        txv4=findViewById(R.id.tv_4);
        txv4.getPaint().setFlags(Paint.STRIKE_THRU_TEXT_FLAG);//中划线
        txv4.getPaint().setAntiAlias(true);//去锯齿
        txv5=findViewById(R.id.tv_2);
        txv5.getPaint().setFlags(Paint.UNDERLINE_TEXT_FLAG);//下划线
```
- 跑马灯
```
		android:singleLine="true"
        android:ellipsize="marquee"
        android:marqueeRepeatLimit="marquee_forever"//一直转
        android:layout_marginTop="15dp"
        android:focusable="true"
        android:focusableInTouchMode="true"/>  //焦点设置
```

## Button
- 大小颜色 和textview一样
- 自定义背景形状   放在background里
  新建drawable资源文件，选shape，设置各属性
```
	<shape xmlns:android="http://schemas.android.com/apk/res/android"
    android:shape="rectangle">
    <solid				//实心
        android:color="#ff9900"
        />
    <corners			//圆角
        android:radius="10dp"
		/>
	<stroke				//边框
        android:width="1dp"
        android:color="#00ff00"
		/>
	</shape>
```
- 自定义按压效果		放在background里
  新建drawable资源文件，选selector，设置属性
```
	<selector xmlns:android="http://schemas.android.com/apk/res/android">

    <item android:state_pressed="true">//按下时
        <shape>							//嵌套shape
            <solid android:color="#CC7A00" />  //改变颜色
            <corners android:radius="5dp" />
        </shape>
    </item>
    <item android:state_pressed="false">//没按时
        <shape>
            <solid android:color="#ff9900"/>
            <corners android:radius="5dp" />
        </shape>
    </item>
	</selector>
```
- 点击事件
  两种方法：
  +Android:onClick属性，给个方法名，然后主函数，记得带View iew
  主函数onCreate中新建个button，findid选中，set监听器，重写onClick,优点是不需要起函数名
- 吐司条显示    `Toast.makeText(this,"我被点击了",Toast.LENGTH_SHORT).show();`