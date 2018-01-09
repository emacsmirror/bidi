# Emacs Bidi

Exploring the Unicode bididirectional algorithm in Emacs Lisp.

The implementation supports *implicit bidirectionality*. The implicit
bidirectional algorithm and the directional marks RLM and LRM are
supported. Full bidirectionality would entail the implicit
bidirectional algorithm, the implicit directional marks, and the
explicit directional embedding codes: RLM, LRM, LRE, RLE, LRO, RLO,
PDF.

The implementation can transform logical to visual order and back. The
visual to logical transformation may be usefull to convert text from
the clipboard, assuming that other applications put text in visual
order into the clipboard.

The bidi code needs BiDiTables that classify characters according to
the bidi types used in the Unicode Tech Report.

The [Unicode Bidirectional Algorithm](https://www.unicode.org/reports/tr9/)
needs tables that classify characters according to the bidi
types used in the Unicode Tech Report, UAX#9. These tables use the
bidi type classification from unicode.org, and it uses this info for
all the 8859 charsets. This is in [bidi-table.el](bidi-table.el) -- about 500k.

There is also a test table which only sets bidi types for ASCII
characters and which uses the bidi type R (like Hebrew and Arabic) for
capital letters. This is great when tinkering with the code and when
writing test cases in plain ASCII. This is in
[bidi-table-test.el](bidi-table-test.el) -- about 5k.

The classification of characters in Emacs relies on Category tables.
In Emacs, these categories can be modified on the Lisp level. Since I
didn't want to reserve any categories, I'm getting some unused
categories when [bidi.el](bidi.el) is loaded. This seems not to work
in XEmacs.
