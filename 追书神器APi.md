#### 追书神器APi   

###获取推荐
http://api.zhuishushenqi.com/book/recommend?gender=male
###获取章节列表
http://api.zhuishushenqi.com/mix-atoc/546039ec39216f8e350b2bbf?view=chapter


book id :
53115e30173bfacb4904897e  
5830f9809d3044887f7fe56e   
508a2727f5cf27d115000001  
50986c0998c8a0890d000015  
5632e5198d12ed2650380753  


###### 推荐列表  
获取书籍相关推荐   
url: http://novel.juhe.im/recommend/:id    
example:  
http://novel.juhe.im/recommend/53115e30173bfacb4904897e  


###### 获取书籍详情  
url: http://novel.juhe.im/book-info/:id   
example: http://novel.juhe.im/book-info/53115e30173bfacb4904897e  

######  获取书籍章节列表
url: http://novel.juhe.im/book-chapters/:id   
example: http://novel.juhe.im/book-chapters/56f8da09176d03ac1983f6cd  

params:

###### 获取章节详细内容
这部分比较复杂：首先使用书籍id获取书源列表，然后选择书源获取章节列表，最后获取章节列表中的link字段url进行编码，作为link传入。
link: 
http://vip.zhuishushenqi.com/chapter/56f8da09176d03ac1983f6d7?cv=1529047156598
http://vip.zhuishushenqi.com/chapter/56f8da09176d03ac1983f6e1?cv=1529047156598
http://vip.zhuishushenqi.com/chapter/56f8da0a176d03ac1983f6e9?cv=1529047156598

###### 获取书籍章节内容  
url: http://novel.juhe.im/chapters/:link 注意这里需要进行url编码   
example: http://novel.juhe.im/chapters/http%3A%2F%2Fvip.zhuishushenqi.com%2Fchapter%2F56f8da09176d03ac1983f6d7%3Fcv%3D1486473051386  



