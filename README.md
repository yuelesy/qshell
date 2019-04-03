# qshell

下载命令行工具（qshell）
------
<br>
 https://developer.qiniu.com/kodo/tools/1302/qshell 下载即可使用

把qshell所在的目录加入到环境变量
------
<br>
如在命令行中输入export PATH = $ PATH：/Users/apple/qshell-v2.3.6/

1.添加密钥和账户名称,AK、SK在七牛个人中心的密码管理，名称为空间名
------
<br>
qshell account < Your AccessKey > < Your SecretKey > < Your Name >
 <br>
添加账号后可以进行查看
<br>
qshell user lookup < Your Name >

2.获取空间所有文件，输出到命令行上
------
<br>
qshell listbucket

3.将这个空间里的所有文件保存到本地
------
qshell listbucket space -o space.list.txt
<br>

4.本地保存的文件进行处理
------
<br>
只需要第一列有文件名的密钥，使用一条awk字符处理命令就可以了
<br>
cat space.list.txt | awk'{print $ 1}'> list.txt list.txt

5.将失效空间的文件复制到新空间（space为失效空间名，test为新建空间名，list.txt为处理后的文件）
------
qshell batchcopy --force --overwrite space text -i list.txt
