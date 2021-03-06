# SliderLayout
<p>SliderLayout 是一款自定义的无限自动轮播滚动控件，可以实现类似于京东淘宝的广告轮播效果。</p>
<p>SliderLayout 具有以下的功能。</p>
<p> 1、可以自定义滚动指示器的样式，扩展性强。</p>
<p>2、同时支持网络图片以及资源图片的加载和显示。</p>
<p> 3、可以自定义控制滚动的时间、是否开启自动轮播等属性。</p>
<p> 4、使用 Picasso 加载图片，同时显示图片的加载提示。</p>
<p> 5、图片的事件监听等均可以扩展。</p>


## Gradle

<p>1、在 Project 的 build.gradle 文件中添加配置，已经发布到 Jcenter，所以只要配置 jcenter 就可以了。</p>

    allprojects {
        repositories {
            jcenter()
        }
    }
<p>2、在 module 下的 build.gradle 文件中添加依赖。</p>

    compile 'com.liuting.sliderlayout:SliderLayout:1.0.1'


## About
<p>1、在布局文件 layout 中写入。</p>

    <com.liuting.sliderlayout.SliderLayout
        android:id="@+id/main_layout_jingdong"
        android:layout_width="match_parent"
        android:layout_height="200dp"
        android:background="@android:color/white"
        app:sl_default_image="@mipmap/ic_default"
        app:sl_indicator_margin="6dp"
        app:sl_indicator_position="centerBottom"
        app:sl_indicator_shape="oval"
        app:sl_indicator_space="3dp"
        app:sl_selected_indicator_color="@android:color/white"
        app:sl_selected_indicator_height="6dp"
        app:sl_selected_indicator_width="6dp"
        app:sl_unselected_indicator_color="@color/unselected_color"
        app:sl_unselected_indicator_height="6dp"
        app:sl_unselected_indicator_width="6dp"
        app:sl_arc_height="0dp"
        ></com.liuting.sliderlayout.SliderLayout>
        
<p>2、在 Activity/Fragment 中直接声明使用。</p>

    SliderLayout layoutImage = (SliderLayout) findViewById(R.id.main_layout_jingdong);
    //设置Dialog提示框样式，用于加载网络图片时进度提示
    layoutImage.setLoadingDialog(dialog);
    //添加图片的点击事件
    layoutImage.setListener(new SliderLayout.IOnClickListener() {
            @Override
            public void onItemClick(View view, int position) {
                Toast.makeText(MainActivity.this,"第 "+(position+1)+" 张图片",Toast.LENGTH_SHORT).show();
            }
        });
<p>3、如果开启了自动滚动的话，在 Activity/Fragment 生命周期 Destroy 的时候记得停止自动滚动。</p>

    @Override
    protected void onStop() {
        layoutImage.stopAutoPlay();
        layoutImage.dismissDialog();
        super.onStop();
    }

<p>4、参考Demo: https://github.com/LT5505/SliderLayout/tree/master/app</p>

<p>5、博客详细介绍：http://www.cnblogs.com/LT5505/p/6652449.html</p>

<p>6、效果图</p>

![效果图](https://github.com/LT5505/SliderLayout/blob/master/Screenhots/10.png?raw=true)

![效果图](https://github.com/LT5505/SliderLayout/blob/master/Screenhots/2.png?raw=true)

![效果图](https://github.com/LT5505/SliderLayout/blob/master/Screenhots/screenshots.gif?raw=true)

<p>最后，感谢开源 https://github.com/dongjunkun/BannerLayout ， https://github.com/florent37/ArcLayout</p>
