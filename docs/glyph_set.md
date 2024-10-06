# 字形集

## `GlyphSet` 类

`GlyphSet` 类用于存储一系列字形，也提供一系列方法来处理这些字形。

## 创建空白字形集

可以使用`init_glyphs`方法创建新的字形集，涵盖某些Unicode编码，但不包含任何字形。

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
