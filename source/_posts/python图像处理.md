---
title: python图像处理--切割（crop函数的运用）
date: 2018-04-16 10:38:44
tags: [python,图像处理]
---

最近在做毕业设计，涉及到图像处理的知识，记录一下

_运行环境python3.6_

先看效果图: 

![img](https://img-blog.csdn.net/2018041708580630?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0hBTk5JTkc1NjMxMjg3NjY=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

可见，这里实现的是一个定点切割，怎么实现的呢？来看看代码：

> from PIL import Image
>
> im = Image.open('F:/test.jpg')
>
> \# 图片的宽度和高度
>
> img_size = im.size
>
> print("图片宽度和高度分别是{}".format(img_size))
>
> left = 80
>
> upper = 210
>
> right = 505
>
> lower = 640
>
> region = im.crop((left,upper,right,lower))
>
> region.save("F:/crop_test.jpg")

这段代码，实现的是从一张大图上切指定区域的某个部分，主要就是利用crop()函数,crop()的参数，而在看了下面这段定义之后，我们应该关注一下crop()函数的这个4-tuple参数了,见crop的定义

>def crop(self, box=None):
>
>​        """
>
>​        Returns a rectangular region from this image. The box is a
>
>​        4-tuple defining the left, upper, right, and lower pixel
>
>​        coordinate.
>
>​        Note: Prior to Pillow 3.4.0, this was a lazy operation.
>
>​        :param box: The crop rectangle, as a (left, upper, right, lower)-tuple.
>
>​        :rtype: :py:class:`~PIL.Image.Image`
>
>​        :returns: An :py:class:`~PIL.Image.Image` object.
>
>​        """

现在具体讲怎么设置(left,upper,right,lower)这个参数，其实简单点来说就是“左上右下”的顺序，我之前那个是怎么实现切割的呢？我是怎么获取这些边界的呢，其实很笨的方法，我使用了ps的坐标，拖动的时候就可以看到对应像素，如下图：

![img](https://img-blog.csdn.net/20180417090642726?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0hBTk5JTkc1NjMxMjg3NjY=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

好了，最简单的切割完成了，在这里在贴一个自动切割多块的代码，切割个数是yy * xx个，可自行修改，知道了原理大家也可以自由发挥哦~效果图和代码如下：

![img](https://img-blog.csdn.net/2018041709134155?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0hBTk5JTkc1NjMxMjg3NjY=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

>from PIL import Image
>
>im = Image.open("F:/test.jpg")
>
>\# 图片的宽度和高度
>
>img_size = im.size
>
>print("图片宽度和高度分别是{}".format(img_size))
>
>xx = 3
>
>yy = 2
>
>x = img_size[0] // xx
>
>y = img_size[1] // yy
>
>for j in range(yy):
>
>​    for i in range(xx):
>
>​        left = i*x
>
>​        up = y*j
>
>​        right = left + x
>
>​        low = up + y
>
>​        region = im.crop((left,up,right,low))
>
>​        print((left,up,right,low))
>
>​        temp = str(i)+str(j)
>
>​        region.save("f:/test/"+temp+".png")

