# آموزش git

<div align="center">
  <img src="https://avatars.githubusercontent.com/u/129286738?s=200&v=4" alt="Homooro" style="width:auto;">
</div>

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

## استفاده از help  
> <code>git command -help</code>  (<em>See all the available options for the specific command</em>)  
> <code>git help --all</code>  (<em>See all possible commands</em>) 

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
> <code>git log --oneline</code>  
> <code>git log --stat</code>  

ویرایش پیام commit انجام شده قبلی :   
> <code>git log --oneline</code>  
> <code>git commit --amend -m "previous commit is replaced with our amended one"</code>  

نمایش **HEAD** در log نشان دهنده آخرین commit انجام شده است.  
</br>  
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
برای اجازه حذف به branch که merge نشده باید از D- استفاده کرد.  
> <code>git checkout master</code>   
> <code>git branch -d test_branch</code>  
> <code>git branch -D test_branch</code>  

تغییر نام branch  
> <code>git branch -m new_branch new_branch2</code>  

ادغام دو branch  
ابتدا وارد branch اصلی می شویم و branch فرعی را با آن ادغام می کنیم.  

> <code>git checkout master </code>   
> <code>git merge develop </code>  

نکته : اگر قبل از تعویض  branch تغییرات آن را commit نکنیم آن تغییرات به branch دیگر منتقل می شود. (کار غلط)  
</br>
## برگشت به نسخه قبل از پروژه  

برگشت به نسخه خاصی از پروژه و مرور کدها (قابل تعویض و تغییر نیست).  
> <code>git log --oneline </code>   
> <code>git checkout <commit_id> </code>  
> <code>git log --oneline </code>  
> <code>git checkout master </code>  

حذف تاثیرات مرتبط با یک commit (خود commit حذف نمی شود) :  
استفاده از دستور revert در log های قدیمی ممکن است باعث ایجاد ارور confilict شود.  
بهتر است دستور revert را در باره ی log های جدید انجام دهیم.  
<div align="center">
  <img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcREslOV3MOQDtRqG21waIy_t9lHL0WQTDBlTeCxK-gTrCdHl9ZYXzb6e4JjTFQpAmRLUNE&usqp=CAU" alt="git revert" style="width:auto;">  
</div>  

> <code>git log --oneline </code>   
> <code>git revert <commit_id> </code>  

دستور reset سه حالت دارد که استفاده از آن نیاز به دقت دارد چراکه تغییرات قابل بازگشت نیست.  
<div align="center">
  <img src="https://www.bogotobogo.com/DevOps/SCM/Git/images/Hard_Reset/three-resets.png" alt="git reverse" style="width:auto;">
</div>  

> <code>git log --oneline </code>   
> <code>git reset <commit_id> --soft</code>  
> <code>git reset <commit_id>  --mixed</code>  
> <code>git reset <commit_id>  --hard</code>  

## کار با فایل gitignore  
نادیده گرفتن یکسری فایل ها و دایرکتوری ها توسط git باید در فایل gitignore. تعریف شود.  

> <code>touch .gitignore</code>  
> <code>git add ./git commit -m "create gitignire file"</code>   
> <code>echo debug.log >> .gitignore </code>  
> <code>git rm --cached debug.log </code>  
> <code>git commit -m "Start ignoring debug.log"</code>  

استفاده از سایت [gitignore](https://www.toptal.com/developers/gitignore) برای ساخت فایل 

## کار با remote ها  
به repository داخلی سیستم local_repository و به repository در سرور خارجی remote_repository می گویند. (مانند github)  
ساخت ssh key در سیستم عامل و اضافه کردن آن به تنظیمات remote(github) جهت شناختن کابر به آن انجام می شود.  

<details dir="rtl">
<summary>راه اندازی ssh key در ویندوز</summary>  
نرم افزار Command Prompt را باز کنید و دستور زیر را در آن تایپ کنید.</br>

> <code>ssh-keygen</code>

به صورت پیش فرض کلید SSh در مسیر C:\Users\your_username/.ssh/id_rsa. ذخیره می شود. برای تایید Enter بزنید.
سپس از شما درخواست میکند برای امنیت بیشتر یک پسورد وارد کنید در صورتی که نمی خواهید پسوردی وارد کنید کافیه دوباره enter بزنید.</br>
پس از ساخته شدن و ذخیره کردن کلید SSH به فولدر مربوطه مراجعه کنید. دو فایل در آن موجود است. فایل id_rsa که پسوندی ندارد و فایل id_rsa.pub که این فایل همان کلیدی است که روی سرورها برای احراز هویت آپلود می‌کنید. فایل اول در حقیقت کلید خصوصی است که می‌بایست از آن حفاظت کنید و در واقع نباید در اختیار کسی قرار بگیرد.</br>
حال وارد تنظیمات ریپازیتوری آنلاینتان شوید و افزودن ssh key را انتخاب کنید و سپس محتویات فایل id_rsa.pub را در آن بریزید.</br>

</details>


<details dir="rtl">
<summary>راه اندازی ssh key در لینوکس</summary>  
اولین مرحله برای تنظیم کلیدهای SSH در اوبونتو، ایجاد یک جفت کلید در ماشین کاربر یا همان کلاینت است:  

> <code>ssh-keygen</code>  

در این مرحله، باید اینتر (Enter) را فشار دهید تا جفت کلید SSH./ را در فضای پیش‌فرض دایرکتوری SSH ذخیره کنید.  همچنین، امکان تعیین مسیر جایگزین وجود دارد.</br>
سپس از شما درخواست میکند برای امنیت بیشتر یک پسورد وارد کنید در صورتی که نمی خواهید پسوردی وارد کنید کافیه دوباره enter بزنید.</br>
پس از اجرای دستور فوق، در آدرس ~/.ssh ، دو فایل id_rsa و id_rsa.pub ساخته می‌شوند که به ترتیب کلید خصوصی(private key) و کلید عمومی(public key) شما می‌باشند.</br>
حال وارد تنظیمات ریپازیتوری آنلاینتان شوید و افزودن ssh key را انتخاب کنید و سپس محتویات فایل id_rsa.pub را در آن بریزید. (دقت کنید که برای دسترسی به این قسمت لازم است که دسترسی مدیر یاadministrative priviledge داشته باشید.)</br>

</details>

</br>  

اضافه کردن پروژه در local به remote_repository :  
 
> <code>git branch -M main</code>   
> <code>git push https://github.com/username/reponame.git main</code>  

ایجاد اسم مستعار به آدرس remote :  
اسم مستعار origin را به ادرس remote معرفی می کنیم.  
> <code>git remote add origin https://github.com/username/reponame.git</code>  
> <code>git branch -M main</code>   
> <code>git push -u origin main</code>  

نمایش اطلاعات remote :  
> <code>git remote -v</code>  
> <code>git remote show origin </code>  

انتقال branch های دیگه به remote :  
> <code>git checkout develop</code>   
> <code>git push origin develop</code>  

بارگیری پروژه ها از سرور بر روی سیستم داخلی
> <code>mkdir myproject</code>  
> <code>cd myproject</code>   
> <code>git clone https://github.com/username/reponame.git </code>  

ریختن از سرور به سیستم محلی  

<div align="center">
  <img src="https://www.edureka.co/community/?qa=blob&qa_blobid=5756095483457844058" alt="git fetch vs pull" style="width:auto;">
</div>  

> <code>git branch -r</code> (<em>see all remote branches</em>)   
> <code>git branch -a</code> (<em>see all local and remote branches</em>)   
> <code>git checkout -b local_branch_name </code>   
> <code>git pull origin remote_branch_name</code>  
 

 ## بررسی تغییرات و حل confilict

ارور confilict ممکن است در local repository یا remote repository رخ دهد. confilict زمانی رخ میدهد که دو شخص همزمان یک قطعه از کد را تغییر دهند.  </br>
## ذخیره تغییرات بدون commit کردن :  
گاهی اوقات مجبوریم یک کار واجب را بدون اینکه تغییرات حال حاضر را commit بزنیم انجام دهیم که از <b>stash</b> استفاده می کنیم.  
> <code>touch test.txt</code>     
> <code>git status</code>   
> <code>git stash/(git stach save "message for create stash")</code>  
> <code>git status</code>     
> <code>git stash list</code>   
> <code>git stash apply id_stash</code>  
> <code>git stash clear</code> (<em>remove all list of stash </em>)  
> <code>git status/git add ./git commit -m "fix stash"</code>   


