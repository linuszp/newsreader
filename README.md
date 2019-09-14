
###### 1.依赖库
过程中需要用到一些开源依赖库文件，先在 build.grade 中声明：


```

    compile 'com.google.code.gson:gson:2.8.0'       //网络解析
    compile 'com.squareup.okhttp3:okhttp:3.7.0'     //网络请求
    compile 'com.github.bumptech.glide:glide:3.8.0' //图片加载
    compile 'com.android.support:design:24.2.1'     //Material Design中用到的依赖库
    compile 'de.hdodenhof:circleimageview:2.1.0'    //显示圆形图片
```
###### 2.网络络请求

在包下创建一个文件夹 util 用来存放工具类，创建文件 HttpUtil.class 用来请求数据：


```
public class HttpUtil {
    public static void sendOkHttpRequest(String address, okhttp3.Callback callback){
        OkHttpClient client = new OkHttpClient();
        Request request = new Request.Builder()
                .url(address).build();
        client.newCall(request).enqueue(callback);
    }
}
```
这里用到的是 okhttp3.Callback 的回调接口，结果会返回到 callback 的回调函数中，后面会进行处理

###### 3.网络解析

这次项目使用的数据来源是天行数据（http://www.tianapi.com/ ）的新闻资讯 API 
![image](https://img-blog.csdn.net/20170506093055476?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQveWl3ZWkxMg==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)

###### 4.效果
![image](https://wx4.sinaimg.cn/mw690/0074AeMrly1g6yzwowq2hg308w0ft4qq.gif)
