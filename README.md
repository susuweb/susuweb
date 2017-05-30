# susuweb
own to susu
遇到一个编程问题，你必须首先想到的是要简化它，简化成一个最简单的问题后，写最简单的代码来解决它，同时只付出最简单的测试代价。

简单HTML源码：

1<!--The loneliest number-->
                        <a>2<!--Can be as bad as one--><b>3


提取上述代码中的注释：

from bs4 import BeautifulSoup, Comment

soup = BeautifulSoup("""1<!--The loneliest number-->
                        <a>2<!--Can be as bad as one--><b>3""")
comments = soup.findAll(text=lambda text:isinstance(text, Comment))

for comment in comments:
    print comment
输出结果：

The loneliest number
Can be as bad as one
去掉上面HTML代码中的注释：

from bs4 import BeautifulSoup, Comment

soup = BeautifulSoup("""1<!--The loneliest number-->
                        <a>2<!--Can be as bad as one--><b>3""")
comments = soup.findAll(text=lambda text:isinstance(text, Comment))
[comment.extract() for comment in comments]
print soup
输出结果：

1
<a>2<b>3</b></a>
