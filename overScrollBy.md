```java
/** 
  * 当滑动的超出上,下,左,右最大范围时回调 
  * 
  * @param deltaX     x方向的瞬时偏移量,左边到头,向右拉为负,右边到头,向左拉为正 
  * @param deltaY     y方向的瞬时偏移量,顶部到头,向下拉为负,底部到头,向上拉为正 
  * @param scrollX    水平方向的永久偏移量 
  * @param scrollY    竖直方向的永久偏移量 
  * @param scrollRangeX  水平方向滑动的范围 
  * @param scrollRangeY  竖直方向滑动的范围 
  * @param maxOverScrollX 水平方向最大滑动范围 
  * @param maxOverScrollY 竖直方向最大滑动范围 
  * @param isTouchEvent  是否是手指触摸滑动, true为手指, false为惯性 
  * @return 
  */
  @Override
  protected boolean overScrollBy(int deltaX, int deltaY, int scrollX, int scrollY, 
                 int scrollRangeX, int scrollRangeY, int maxOverScrollX, 
                 int maxOverScrollY, boolean isTouchEvent) { 
    return super.overScrollBy(deltaX, deltaY, scrollX, scrollY, 
        scrollRangeX, scrollRangeY, maxOverScrollX, maxOverScrollY, 
        isTouchEvent); 
  } 
```


[来自](https://www.jb51.net/article/120240.htm)
