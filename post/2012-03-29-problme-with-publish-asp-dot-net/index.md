
今天在发布一个网站的时候,遇到了一些问题:

1.  `xx is not allowed here because it does not extend class 'System.Web.UI.Page'. 出现该问题的原因是由于页面的namespace错误导致的.修改为和web项目一直的就可以了.
2.  asp.net从2.0开始,默认是不允许从文本框中提交xml的,认为可能会引发安全问题.不过的确如此.但是是在不需要的时候.可以通过在web.confg里面加入 
    <pre>&lt;pages validateRequest="false"/>
</pre>来解决.