
## Matlab

前些日子帮女朋友分析了点实验的数据，就是用matlab做了线性拟合。用到`polyfit`这个函数，`ployfit`是专门用来做多项式的线性拟合的。 是基于最小二乘法计算的。

```matlab
x=[0 20 40 60 100 130 160 190];
y=[18 17.586 17.136 16.704 15.84 15.129 14.544 13.896];
a=polyfit(x,y,1);
xi=0:0.001:200;
yi=polyval(a,xi);
plot(x,y,'go','MarkerEdgeColor','k','MarkerFaceColor','g','MarkerSize',6)
xlabel('深度/m','fontsize',16);<br />
ylabel('温度/℃','fontsize',16);
axis([0 200 12 20])
hold on
plot(xi,yi,'linewidth',2,'markersize',16)
legend('原始数据点','拟合曲线')
sprintf('直线方程：Y=%0.5gxX+%0.5g',a(1),a(2))
```

自己邮箱里面还有如何实现最小二乘法的M文件。。。一晃N年没有写过M文件了。现在还是觉得`5.4`的版本很经典，小巧而且常用的功能都有了。

## OriginLab

`OriginLab`使用的线性拟合的算法应该是和`Matlab`一样。得出的结果也是一样的，不过操作起来简单许多。点点鼠标就可以完成了。这点还是很强悍的。而且可以引入M文件来进行计算。后面会好好学学，为了应付女朋友派下来的工作。