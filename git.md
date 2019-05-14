git init  
git clone  
git status  
git log  
git add .   
git diff  
git commit  
git reset   // git reset --soft HEAD~ 上一步 , --hard 哈希值 强制回到指定提交记录处 , 回滚   
git revet HEAD  撤销最近一个提交 //生成新版本   
git branch   
git checkout   
git fecth   
git merge   
git remote   
git push   
git pull  //  git pull会首先执行git fetch,然后执行git merge,把取来的分支的head merge到当前分支.这个merge操作会产生一个新的commit.   

###### demo 
```
echo "# demo" >> README.md  
git init
git add README.md
git commit -m "first commit"
git remote add origin git@github.com:arjun512/demo.git
git push -u origin master
```

`git remote remove origin`  del origin 





