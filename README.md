# AnnoAndSendMsg
一个基于反射的注解和消息机制的简易框架

#使用说明

如果你想使用它将basemodel导入你的项目,acitivity继承BaseActivity 这样你就可以使用了


在你所写的acitivity类的上方加上@LayoutView(R.layout.activity_main)即可将布局注入到acitivity中


控件@BindViews(R.id.tv)
    TextView tv; 这样即可省略findviewbyid这已亢长的代码
    
    
如果你想实现某个控件的点击事件  @Click({R.id.bt,R.id.bt1})
    public void initClick(View view){
       switch (view.getId()){
       }
    } 在这一步先初始化控件 然后再设置点击事件,注意方法中的View view参数必须带着不然会报错.
    
    
 Fragment还没写 道理通activity一样
 
 
#消息机制
 这个消息机制是基于rxjava的
 
 注册消息 @MsgAction(name = "aaa")
    public void getMsg(Object object) {
    }得到的消息将调到getMsg方法中 object即为得到的消息
    
    

 发送消息
    
 new Message.Builder().name("aaa").Content(object).send();调用这个函数将消息进行发送  name 为注册时的name.
 content方法即为消息内容 采用buildler模式进行发送.
    
    
 消息机制暂时只能在继承BaseActivity中使用 得到的消息回调到主线程.
