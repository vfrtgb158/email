  # py3_email
 通过对smtplib和email模块进一步封装成py3_email.
 py3_email超简单,超易用. 以近乎傻瓜式的方式发送纯文本/图像/html邮件,并可添加附件

 from py3_email import Mail 导入模块

 # 创建邮件对象
 m=Mail(host,user,password,receivers)
 这里假设本机未安装SMTP服务(事实上绝大多数使用者都没有),所以使用代理发送邮件

         :param receivers: 接收邮箱,如果有多个用列表
         :param host: SMTP邮件服务器 eg smtp.qq.com,如果本机有安装可用localhost
         :param user: 登陆该邮箱的用户名
         :param password: 密码
         :param sender: 默认为user,可以设置为其他邮箱

 # 一、发送纯文本邮件
 添加纯文本邮件非常简单，只需要用.add_text(text)方法,且参数只有一个text
  + m.add_tittle(title='测试标题')
  + m.add_text('这是使用python发送的测试邮件...\n'
            '这是一封纯文本的邮件,不带任何图片')
  + m.send()


 # 二、添加附件
 添加附加只需用add_attachment()方法,如果想添加n个附件,重复这个方法n次即可
  + m.add_attachment('test1.txt')
  + m.add_attachment('test2.txt')
  + m.add_attachment('test.jpg')
  + m.add_attachment('test.png')
  + m.send()

 # 三、发送HTML
 发送超链接也超级简单，用add_html()方法,唯一的参数是html_text
  + html_text = r"<h>Python 邮件发送测试...</h><p><a href="https://github.com/vfrtgb158/email/tree/master">这是一个超链接</a></p>"
  + m.add_html(html_text)
  + m.send()

 # 四、添加图片
 把图片添加到附件里，可能并不是你想要的效果，或许你想要的是在邮件正文中把图片展示出来，仅此而已。
 这种情况，需要把图片放在HTML中，怎么做？
 py3_email得意的告诉你，so easy！
  + html_text = """
  +     <h>Python 邮件发送测试...</h>
  +     <p><a href="https://github.com/vfrtgb158/email/tree/master">这是一个超链接</a></p>
  +     <p>下面是2张图片：</p>
  +     <p><img></p>
  +     <p><img></p>
  +     """
  + m.add_img('test.jpg')
  + m.add_img('test.png')
  + m.add_html(html_text)
 你想要添加几张图片就在html_text中埋下几个<img>标签
 请保持添加图片的数量和<img>的数量一致
 py3_email会按照图片添加的顺序放入对应的<img>处
 记得,要先添加图片哦

 # 五、给自己来个漂亮的昵称
  + add_tittle() 方法填上from_nickname参数,昵称由你来定
  + m.add_tittle(title='测试标题',from_nickname='noreply')

 # 六、本地已安装SMTP的使用方法
 只需要填写初始化示例时只需要填写host（一般为localhost），sender（发送邮箱）
 其他不变

 # 七、写在最后
 还记得用py3_email发送电子邮件的过程吗
 1.建立Mail对象
 2.添加主题:add_tittle
 3.添加纯文本邮件:add_text(纯文本模式与html模式只能用一个)
 4.添加附件或图片:add_attrament/add_img
 5.添加html语句:add_html
 6.发送:send


 怎么样有感觉到py3_email的魅力了吗，赶紧安装体验吧
 如果使用中遇到什么问题，可以在下方留言
 如果觉得好用的老铁，可以点个赞，也可以跟我一起让py3_email更加完善
