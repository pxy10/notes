## BeautifulSoup Documents for web scawler

[doc](https://www.crummy.com/software/BeautifulSoup/bs4/doc.zh/#id15)

BeautifulSoup可以帮助从HTML或XML文件中提取数据

```python
from bs4 import BeautifulSoup
soup = BeautifulSoup(html_doc)
print(soup.prettify()) #按照标准缩进格式输出
```

Beautiful Soup将复杂HTML文档转换成一个复杂的树形结构,每个节点都是Python对象,所有对象可以归纳为4种: Tag , NavigableString , BeautifulSoup , Comment.

### Tag

tag对象即为原生文档中的tag. 也即文档中`<tag>`表示的内容, 结尾为: `/tag`.

#### tag的获取和查找

通过`soup.find('tag')`, `soup.find_all('tag')`, `soup.select('tag')`的方式都可以获取. 如果已知tag, 通过`soup.tag`的方式也可以获取tag数据. 但是`.find`和`.tag`的方式都只是获取第一个出现该tag的数据. 如果该tag数据下还有子tag, 可以采用上述方式进一步获取: `tag.find('subtag)`等,

对于Tag类型的数据, 通过`.name`和`.attrs`可以分别获取tag的名字和属性.

对于子节点, 可以通过`.contents`以列表的方式输出, 通过tag的 `.children`生成器,可以对tag的子节点进行循环:

```python
for child in title_tag.children:
    print(child)
```

这种方法只包含了第一层子节点, 对于后面几层子孙节点, 可以通过`.descendants`获取, 使用方法与`.children`类似.

`.parent`可以获取父节点. 
