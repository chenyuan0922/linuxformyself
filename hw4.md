# HW4
### 使用ubuntu

1</br>

* 建立群組 mygroup、nogroup，grep查看group是否存在</br>
<pre><code>groupadd mygroup
grep mygroup /etc/group</code></pre>
![01](img/01.png)</br>
* 建立帳號 myuser1~3，加入 mygroup，密碼為 MyPassWord，2、3以此類推</br>
<pre><code>useradd -m -G mygroup myuser1
passwd myuser1</code></pre>
![02](img/02.png)</br>
* 建立帳號 nouser1~3，加入 nogroup，密碼為 MyPassWord，2、3以此類推</br>
<pre><code>useradd -m -G nogroup myuser1
passwd nouser1</code></pre>
![03](img/03.png)</br> 
* 切換至myuser1 前往 /srv/myproject 建 myproject.data</br>
先更改權限</br>
<pre>chgrp mygroup myproject
chmod 770 myproject</pre>
![04](img/04.png)</br>
再進入 myuser1</br>
<pre>touch myproject.data</pre>
![05](img/05.png)</br>
* 復制/usr/bin/ls至/usr/local/bin/myls...</br>
<pre>cp -r /usr/bin/ls /local/bin/myls
chmod 4755 myls</pre>
![06](img/06.png)</br>

2</br>
<pre>ps aux | grep rsyslog
ps aux | grep rsyslog > /root/preocess_syslog.txt
cat /root/process_syslog.txt</pre>
grep 分類查詢</br>
>重新導向至後面內容</br>
cat 查看後面檔案內容</br>
![07](img/07.png)</br>

3</br>
<pre>find /usr/bin -perm /u=s</pre>
find 是主要使用的搜尋指令 後面加查詢事物</br>
-perm 是指定檔案權限</br>
/u=s 即為 含有SUID的特殊檔案</br>
![08](img/08.png)</br>
<pre>find /usr/bin -perm /u=s -ok ls -l > findsuidsgid.txt
find /usr/bin -perm /u=s -ok ls -l 1>> findsuidsgid.txt</pre>
兩句差別在 > 1>></br>
上面是顯示每筆，下面則是顯示一筆</br>
![09](img/09.png)</br>
<pre>cat findsuidsgid.txt</pre>
![10](img/10.png)</br>
