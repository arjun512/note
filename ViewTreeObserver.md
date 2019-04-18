###### ViewTreeObserver的OnGlobalLayoutListener
优点：不需要额外的测量过程
缺点：只有在布局加载完成后，才能得到宽和高
OnGlobalLayoutListener是ViewTreeObserver的内部类，当一个视图树的布局发生改变时，可以被ViewTreeObserver监听到，这是一个注册监听视图树的观察者(observer)，在视图树的全局事件改变时得到通知。ViewTreeObserver不能直接实例化，而是通过getViewTreeObserver()获得。
其中，我们可以利用OnGlobalLayoutListener来获得一个视图的真实高度，但是需要注意的是OnGlobalLayoutListener会被多次触发，因此在得到了高度之后，要将OnGlobalLayoutListener清除掉。
```java    private void measureWidth() {
        //对控件layout结束事件进行监听（也不知道到底是先布局子空间还是父控件）
        view.getViewTreeObserver().addOnGlobalLayoutListener(new OnGlobalLayoutListener() {
            @Override
            public void onGlobalLayout() {// 当layout执行结束后回调
                //使用完必须撤销监听（只测量一次），否则，会一直不停的不定时的测量，这比较耗性能
                view.getViewTreeObserver().removeOnGlobalLayoutListener(this);//Added in API level 16
                //view.getViewTreeObserver().removeGlobalOnLayoutListener(this);//废弃了
                int width = view.getMeasuredWidth();
                int width2 = view.getWidth();//和上面的值是一样的
            }
        });
    }  
```

这种方法无法像第一种方法那样通过一个函数返回值，因为他是基于listener的，OnGlobalLayoutListener的onGlobalLayout被回调之前是没有值的。
由于布局状态可能会发生多次改变，因此OnGlobalLayoutListener的onGlobalLayout可能被回调多次，所以我们在 第一次获得值之后就将listener注销掉。 

###### ViewTreeObserver的内部回调接口：

OnGlobalLayoutListener    当在一个视图树中全局布局发生改变或者视图树中的某个视图的可视状态发生改变时回调

OnPreDrawListener    当一个视图树将要绘制时，所要调用的回调函数的接口类

OnScrollChangedListener    当一个视图树中的一些组件发生滚动时回调

OnGlobalFocusChangeListener    当在一个视图树中的焦点状态发生改变时回调

OnTouchModeChangeListener    当一个视图树的触摸模式发生改变时回调

###### 回调方法：

addOnGlobalFocusChangeListener 当在一个视图树中的焦点状态发生改变时调用

addOnGlobalLayoutListener 当在一个视图树中某个视图的可视状态发生改变时调用

addOnPreDrawListener 当一个视图树将要绘制时调用

addOnScrollChangedListener 当一个视图发生滚动时调用

addOnTouchModeChangeListener 当一个触摸模式发生改变时调用

dispatchOnGlobalLayout 当整个布局发生改变时通知相应的注册监听器

dispatchOnPreDraw 当一个视图树将要绘制时通知相应的注册监听器

isAlive 指示当前的ViewTreeObserver是否可用

removeGlobalOnLayoutListener 移除之前已经注册的全局布局回调函数

removeOnGlobalFocusChangeListener 移除之前已经注册的焦点改变回调函数

removeOnPreDrawListener 移除之前已经注册的预绘制回调函数

removeOnScrollChangedListener 移除之前已经注册的滚动改变回调函数

removeOnTouchModeChangeListener 移除之前已经注册的触摸模式改变回调函数


[link](https://blog.csdn.net/lihappyangel/article/details/52870784)
