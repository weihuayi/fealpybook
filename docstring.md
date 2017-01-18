
# PYTHON 注释写作标准
## Docstring 标准

一个文档字符串是用来描述模块，函数，类或方法的字符串，这个字符串是一个对象的特殊属性，由三个双引号所围成：
```
"""
This is the form of a docstring!

It can be spread over several lines.
"""
```
## Section
1. 短的概要
  * 不使用函数名或变量名的一行概要，例如:
```
def add(a,b)
    """
    The sum of two numbers.
    """
```
  * 函数名通常通过内行查找或者通过帮助显示，对于某些函数名不可用，因此我们不得不把它写到字符串里第一行
```
    """
    def add(a,b)
    The sum of two numbers.
    """
```
1. 弃用警告
这一部分是警告用户对象已经被弃用。包含了:
  * numpy 中什么对象被弃用，什么时候被弃用的
  * 弃用的原因是什么
  * 得到相同功能的推荐方法
1. 扩展概要
这部分被用于说明功能，而不是讨论细节和背景理论，可以推断出参数和函数名，但参数描述仍属于参数部分
1. 参数
  * 函数参数，关键词和他的相关类型的描述
```
Parameters
－－－－－－－－
   x : type
       Description of parameter `x`.
   y
       Description of parameter `y` (with type not specified)
```
将变量括在单个反引号中. 冒号必须以空格开头，如果类型不存在，则会省略.
  * 对于参数类型要尽可能的准确，例:
```
Parameters
－－－－－－－－
   filename : str
   copy : bool
   dtype : data-type
   iterable : iterable object
   shape : int or tuple of int
   files : list of str
```
  * 如果不需要指定关键参数，要用可选择的
```
x : int, optional
```
  * 当参数只能假设一组固定值中的一个，这些值可以列在大括号中，默认显示在第一个值
```
order : {'C', 'F', 'A'}
    Description of `order`
``` 
  * 当两个或多个输入参数有相同的类型，形状，描述，则可以结合在一起
```
x1, x2 : array_like
    Input arrays, description of `x1`, `x2`.
```
1. 返回
  * 返回值及类型的说明，类似参数部分除了返回值的名字，都是可选的，每个返回值的类型总是必须的.
```
Returns
－－－－－－
int
    Description of anonymous integer return value.
```
  * 如果名字和类型指定返回值部分，采用与参数部分相同的形式
```
   Returns
   －－－－－－
   err_code : int
      Non-zero value indicates error code, or zero on success.
   err_msg : str or None
      Human readable error message, or None on success.
```
1. `Yields`
  * 所产生的值的类型及其类型的说明，同返回部分类似，每个值的名字是可选的，但每个值的类型是必须的
```
   Yields
   －－－－－
   int
      Description of the anonymous integer return value
```
  * 如果同时指定了名称和类型，`Yields`部分的格式与`Returns`部分相同：
```
   Yields
   －－－－－
   err_code : int
      Non-zero value indicates error code, or zero on success.
   err_msg : str or None
      Human readable error message, or None on success.
```
1. 其他的参数
用于描述不常使用的参数的可选部分. 只有在函数具有大量关键字参数时，才应使用它，以避免使“参数”部分变得混乱.
1. `Raises`
一个可选的部分，详细说明在什么条件下生成错误
```
Raises
－－－－－
LinAlgException
    If the matrix is not numerically invertible
```
1. `See Also`
  * 用于引用相关代码的可选部分，这部分也是非常有用的，但应该谨慎使用，目标是将用户引导到他们，没有意识到其他的功能，其文档字符串进一步解释了此函数使用的参数，例如
```
See Also
－－－－－－－
average : Weighted average
```
  * 当在同一子模块下引用函数时，不需要前缀并且向上搜索树以上进行匹配，其他子模块的前缀功能，例如:
```
fft.fft2 : 2-D fast discrete Fourier transform
```
1. `Notes`
  * 提供了代码的额外信息，包括标准的讨论可以包含数学方程：
```
The FFT is a fast implementation of the discrete Fourier transform:
.. math:: X(e^{j\omega } ) = x(n)e^{ - j\omega n}
```
  * 可以内联使用数学：
```
The value of :math:`\omega` is larger than 5.
```
  * 变量名以`typewriter`字体显示，用`mathtt{var}`获得，允许使用图像，但不应该是解释的核心，用户看文档应该理解其含义，无需诉诸图像查看器，附加说明包括
```
.. image:: filename
```
1. 参考
在注释部分中引用的参考文献可以在此列出. 如果你引用下面的文章使用文本[1] ，包括它在列表如下
```..[1] O. McNoleg, "The integration of GIS, remote sensing,
   expert systems and adaptive co-kriging for environmental habitat
   modelling of the Highland Haggis using object-oriented, fuzzy-logic
   and neural-network techniques," Computers & Geosciences, vol. 22,
   pp. 585-588, 1996.
```
1. 例子
一个可选部分的示例，使用`doctest`格式. 这部分是为了说明用法，而不是提供一个测试框架，为此，使用`tests /`目录. 虽然是可选的，但非常鼓励这一部分.
  * 当提供多个示例时，它们应该由空行分隔. 解释示例的注释应该在其上方和下方都有空行：
```
>>> np.add(1, 2)
3
>>> np.add([1, 2], [3, 4])
array([4, 6])
```
  * 对于具有随机或平台相关的结果的测试，将输出标记为：
```
>>> import numpy.random
>>> np.random.rand(2)
array([ 0.35773152,  0.38568979])  #random
```
  * 您可以使用以下命令来运行示例：
```
>>> np.test(doctests=True)
>>> np.linalg.test(doctests=True)  # for a single module
```
  * 在`IPython`中，也可以通过在`doctest`模式下复制粘贴来运行个别示例：
```
In [1]: %doctest_mode
Exception reporting mode: Plain
Doctest mode is: ON
>>> %paste
 import numpy.random
 np.random.rand(2)
array([ 0.8519522 ,  0.15492887])
```
  * 没有必要使用`doctest`标记<BLANKLINE>在输出中指示空行. 注意，提供了通过`numpy.test`运行示例的选项，用于检查示例是否工作，而不是使示例成为测试框架的一部分.

## 类docstring
使用与上述相同的部分. 构造函数（`__init__`）也应该在这里记录，`docstring`的参数部分详细描述了构造函数的参数.

  * 位于参数部分下方的属性部分可用于描述类的非方法属性
```
Attributes
－－－－－－－－
x : float
    The X coordinate.
y : float
    The Y coordinate
```
  * 作为属性并具有自己的`docstrings`的属性可以按名称简单列出：
```
Attributes
－－－－－－－－
real
imag
x : float
    The X coordinate
y : float
    The Y coordinate
```
  * 一般来说，没有必要列出类方法. 那些不是公共`API`的一部分的名称以下划线开头. 然而，在一些情况下，类可以具有许多方法，其中只有少数是相关的（例如，`ndarray`的子类）. 然后，有一个额外的方法部分变得有用.
```
class Photo(ndarray):
    """
    Array with associated photographic information.

    ...

    Attributes
    ----------
    exposure : float
        Exposure in seconds.

    Methods
    -------
    colorspace(c='rgb')
        Represent the photo in the given colorspace.
    gamma(n=1.0)
        Change the photo's gamma exposure.

    """
```
如果有必要解释私有方法（小心使用！），则可以在扩展摘要或注释部分中参考. 不要在方法部分列出私有方法.

请注意，self不作为方法的第一个参数列出.
## Method docstrings
记录这些，因为你会有任何其他功能. 不要在参数列表中包含`self`. 如果一个方法有一个等效的函数（例如对于许多`ndarray`方法的情况），函数`docstring`应该包含详细的文档，并且方法`docstring`应该引用它. 只在方法`docstring`中提供简要摘要和另请参见部分.

## 记录类实例
作为`NumPy API`（例如`np.r_ np，c_，np.index_exp`等）一部分的类的实例可能需要一些注意. 为了给这些实例一个有用的`docstring`，我们做以下：

* 单个实例：如果只暴露一个类的单个实例，请记录该类. 示例可以使用实例名称.
* 多个实例：如果暴露了多个实例，则会在运行时写入每个实例的`docstrings`并将其分配给实例的`__doc__`属性. 类照常记录，暴露的实例可以在`Notes`和`See Also`部分中提及.
## 记录生成器

应该记录生成器，就像记录功能一样. 唯一的区别是，应该使用`Yields`部分而不是`Returns`部分. 支持`Yields`部分在`numpydoc`版本0.6中添加.

## 记录常量

使用与功能相同的部分
```
1. summary
2. extended summary (optional)
3. see also (optional)
4. references (optional)
5. examples (optional)
```
常量的文档字符串在文本终端中将不可见（常量是不可变类型，因此不能像类实例一样为其分配`docstrings`），但会出现在使用`Sphinx`构建的文档中.
## 记录模块
每个模块应该有一个`docstring`，至少有一个摘要行. 其他部分是可选的，并且在文档功能适当时应按照与文档功能相同的顺序使用：
```
1. summary
2. extended summary
3. routine listings
4. see also
5. notes
6. references
7. examples
```

鼓励常规列表，特别是对于大型模块，对于通过查看源文件或`__all__`命令提供的所有功能很难得到良好的概述.

请注意，许可证和作者信息通常包含在源文件中，不属于`docstrings`.

## 其他要点要记住
1. 方程：如上面的注释部分所讨论的，`LaTeX`格式应保持最小. 通常，可以将方程式显示为`Python`代码或伪代码，这在终端中更加可读. 对于在线显示使用双反引号（如`y = np.sin（x）`）. 对于上面和下面的空白行显示，使用双冒号和缩进代码，如：
```
end of previous sentence::
    y = np.sin(x)
```
1. 注意和警告：如果文档字符串中有要特别强调的点，那么可以在警告上下文（部分内）的附近使用注释或警告的`reST`指令. 句法：

```
.. warning:: Warning text.

.. note:: Note text

```
1. `array_like:`对于拥有不仅具有类型`ndarray`的参数，而且还可以转换为`ndarray`（即标量类型，序列类型）的类型的函数，可以使用类型`array_like`记录这些参数.
## 常见的`reST`概念
1. 对于段落，缩进是有意义的，并指示输出中的缩进. 新段落用空行标记.
1. 如果需要在任何解释中使用`* italics *，** bold **`和``monospace``（但不是变量名和`doctest`代码或多行代码）. 变量，模块，函数和类名应该写在单个回零（`numpy`）之间.
1. 在本示例文档中可以找到更广泛的`reST`标记示例; 快速参考在编辑时很有用.线间距和缩进是重要的，应该仔细遵循.
## 结论
此处显示的格式示例可用. 有关如何使用`Sphinx`构建手册，请参考如何构建`API /`参考文档.

这个文档本身是用`ReStructuredText`编写的，并且可以使用：
```
$ rst2html HOWTO_DOCUMENT.txt HOWTO_DOCUMENT.html
```














