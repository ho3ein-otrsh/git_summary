# آموزش git

## آماده سازی ابتدایی git در سیستم
 
> <code>git config --global user.name "Myname"</code>  
> <code>git config --global user.email "Myemail@gmail.com"</code>  
> <code>git config --list/-l</code>  

<p>شناساندن یک پوشه به git</p>

> <code>mkdir project</code>  
> <code>cd project/</code>  
> <code>git init</code>  

فایل git. در همان پوشه ساخته می شود که حاوی اطلاعات و تنظیمات پروژه است.  

<p>نمایش وضعیت پروژه </p>  

> <code>git status</code>  

## اضافه کردن فایل به پروژه و ثبت تغییرات

<div align="center">
  <img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTjUMKlOAdFOWaBW_Dk8Odg2AZipZo2b49RsvsKOeqPXLYC_8tvRH80Byc4HMu1rnaM714&usqp=CAU" alt="git add" style="width:auto;">
</div>
به طور مثال : ساخت فایل  

> <code>touch a.txt</code>  
> <code>git status</code>  
> <code>git add a.txt</code>  
> <code>git status</code>  
> <code>git commit -m "add file a.txt "</code>  
> <code>git status</code>  

اصلاح فایل و نوشتن در آن  
> <code>echo "this is a new line" > a.txt</code>  
> <code>cat a.txt</code>    
> <code>touch b.txt</code>  
> <code>git status</code>  
> <code>git add ./-A</code>   
> <code>git commit -m "modified file a.txt and create b.txt"</code>  
> <code>git status</code>  

برگردان فایل ها در stage به حالت unstage

> <code>echo "this is a new line" > b.txt</code>     
> <code>git add .</code>  
> <code>git status</code>  
> <code>git restore --stage b.txt </code>  
> <code>git status</code>   

دیدن تاریخچه commit ها

> <code>git log</code>  
> <code>git log --online</code>  
> <code>git log --stat</code>  

نمایش **HEAD** در log نشان دهنده آخرین commit انجام شده است.

## کار با branch ها

<div align="center">
  <img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTFKUtCq_zsUm4gX7FwWydZ99wzZLUDv0R45hgdoB3_5BAyEmbPt5qXPB7RzDRXfYBjTf0&usqp=CAU" alt="git branch" style="width:auto;">
</div>

به شاخه اصلی پروژه master یا main می گویند.  

نمایش لیست branch ها :  
> <code>git branch</code>  
> <code>git branch --list/-l</code>  

ساخت branch جدید  
> <code>git branch new_branch</code>  
> <code>git checkout new_branch</code>  

ساخت و تعویض سریع branch  
> <code>git checkout -b test_branch</code> 

حذف branch   
> <code>git checkout master</code>   
> <code>git branch -D test_branch</code>  

تغییر نام branch  
> <code>git branch -m new_branch new_branch2</code>  

ادغام دو branch  