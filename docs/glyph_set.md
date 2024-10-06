# 字形集

## `GlyphSet` 类

`GlyphSet` 类用于存储一系列字形，也提供一系列方法来处理这些字形。

## 创建空白字形集

可以使用`init_glyphs`方法创建新的字形集，涵盖某些Unicode编码，但不包含任何字形。

传入的

```python
from unicode_utils import GlyphSet

glyph_set = GlyphSet.init_glyphs(range(0x0000, 0x10FFFF))
```
