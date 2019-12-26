# email
通过对smtplib和email模块进一步封装成pymail. pymail超简单,超易用. 以近乎傻瓜式的方式发送纯文本/图像/html邮件,并可添加附件

from pymail import Mail 导入模块

# 创建邮件对象
m=Mail(host,user,password,receivers)  
这里假设本机未安装SMTP服务(事实上绝大多数使用者都没有),所以使用代理发送邮件

        :param host: SMTP邮件服务器 eg smtp.qq.com
        :param user: 登陆该邮箱的用户名
        :param password: 密码
        :param receivers: 接收邮箱,如果有多个用列表
        :param sender: 默认为发送者邮箱
        
      
