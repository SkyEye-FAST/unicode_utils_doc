# 字形集

## `GlyphSet` 类

`GlyphSet` 类用于存储一系列字形，也提供一系列方法来处理这些字形。

## 创建空白字形集

直接实例化`GlyphSet`类可以创建一个空白字形集。

```python
>>> from unicode_utils import GlyphSet
>>> glyph_set = GlyphSet()
```

但是这样创建的字形集不包含任何Unicode编码位点。我们可以使用`init_glyphs`方法创建新的字形集，在实例化时就涵盖某些Unicode编码，而不必先准备相应的字形。

编码范围中的元素必须为有效的Unicode编码（参见[`Glyph`类的说明](glyph.md#glyph类)），否则会抛出`ValueError`异常。

如果传入的编码范围为`list`类型，那么其中的元素必须为`int`或`str`类型，否则会抛出`TypeError`异常。

```python
>>> from unicode_utils import GlyphSet
>>> glyph_set = GlyphSet.init_glyphs([0x41, 0x42, "43", "0050", 0x55, "76"])
```

传入的编码范围也可以是`range`对象。

```python
>>> glyph_set = GlyphSet.init_glyphs(range(0x4E00, 0x9FA5))
```

## 向字形集中添加字形

可以使用`add_glyph`方法向字形集中添加字形。

添加的字形必须为`Glyph`对象[^1]，否则会抛出`TypeError`异常。

```python
>>> from unicode_utils import Glyph, GlyphSet
>>> glyph_set = GlyphSet()
>>> glyph = Glyph("5B57")
>>> glyph_set.add_glyph(glyph)
```

可以使用加法运算符（`+`）来合并两个`GlyphSet`对象，得到的新`GlyphSet`对象中包含原先的两个字形集中的字形。

在运算时，`+`后面的字形集，会覆盖`+`前面的字形集中的字形。例如，下方的例子中，`glyph_set_2`会覆盖`glyph_set_1`中的字形。

```python
>>> glyph_set_1 = GlyphSet.init_glyphs([0x41, 0x42])
>>> glyph_set_2 = GlyphSet.init_glyphs([0x41, 0x43, 0x44])
>>> glyph_set = glyph_set_1 + glyph_set_2
```

也可以使用原地加法（In-place Addition，即`+=`运算符）来添加字形或字形集。

```python
>>> glyph_set += glyph
>>> glyph_set += glyph_set_1
```

两个`Glyph`对象相加可以得到一个`GlyphSet`对象，其中包含原先的两个字形。

```python
>>> from unicode_utils import Glyph, GlyphSet
>>> glyph_1 = Glyph(0x4E00)
>>> glyph_2 = Glyph(0x4E01)
>>> glyph_set = glyph_1 + glyph_2
```

[^1]: 为了保证兼容性，这里也可以传入格式为`(code_point, hex_str)`的元组，但不推荐这样做——除非你在某些特殊情况下无法创建`Glyph`对象。
