# 编辑器

本项目还提供了一些CLI程序，可直接在终端中修改字形。编辑的结果可以在代码中继续使用，不必中途易辙。

这些CLI程序使用跨平台的框架[Textual](https://textual.textualize.io/)编写，对终端的要求不高。不过，仍然建议使用比较现代的终端来运行它们。

## `GlyphEditor`

`GlyphEditor`可以用来编辑字形，需要传入`Glyph`对象。

编辑完成后退出编辑器，传入的`Glyph`对象会自动更新。可以在代码中继续处理编辑后的字形。

下面以字符“過”（U+904E）为例：

``` python
>>> from unicode_utils import Glyph, GlyphEditor
>>> glyph = Glyph("904E")
>>> glyph.load_hex("01F8210811E81128012803FCF20412F4129412F4120412141208280047FE0000")
>>> GlyphEditor(glyph).run()
```

此时，终端的显示应当类似于下图：

![GlyphEditor](image/GlyphEditor_1.svg)

中央为字形编辑区，上方为该字符的Unicode名称、编码和字符本身，下方的坐标为光标目前所在的位置。

`GlyphEditor`的操作方式和常见的图片编辑器类似，可以使用键盘或鼠标操作它。

### 使用键盘操作

|        按键        |       名称       |           解释           |
| ------------------ | ---------------- | ------------------------ |
| ++w++ / ++up++     | Up               | 向上移动光标             |
| ++s++ / ++down++   | Down             | 向下移动光标             |
| ++a++ / ++left++   | Left             | 向左移动光标             |
| ++d++ / ++right++  | Right            | 向右移动光标             |
| ++space++          | Toggle 0/1       | 改变当前位置像素的可见性 |
| ++q++ / ++ctrl+c++ | Quit             | 退出编辑器               |
| ++ctrl+d++         | Toggle Dark Mode | 切换浅色/深色模式        |

### 使用鼠标操作

编辑器光标会跟随鼠标指针移动，左键单击可以将像素的值设置为`1`，右键单击则可以设为`0`。

和在常见的图片编辑器中一样，`GlyphEditor`中也可以按住鼠标左键或右键并拖动，光标经过的像素会被一同设置。

## `GlyphReplacer`

`GlyphReplacer`可以用来交互式替换字形，需要传入`Glyph`对象和查找、替换所用的图案。

![GlyphReplacer](image/GlyphReplacer_1.svg)

使用方法请见[替换](replace.md)一文的说明。
