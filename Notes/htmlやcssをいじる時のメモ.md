---
aliases: []
tags: []
publish: true
date: 2023-05-04T10:13:48+09:00
updated: 2023-05-04T10:22:05+09:00
---

- htmlやCSSの各種タグやプロパティの意味を調べるには[MDN Web Docs](https://developer.mozilla.org/ja/)で検索するのが早い

## CSS selector

### selectorの使い分け
- [CSS 複数のセレクタを指定する/絞り込むサンプル \| ITSakura](https://itsakura.com/css-multi-selector#s2)

階層構造でセレクタを指定する[^1]
-  `ul li`
- `ul > li`
-  `ul + ul`
-  `ul ~ ul`
Example checklist:
-  `ul li` - _**Looking inside**_ - Selects **all** the `li` elements placed (anywhere) inside the `ul`; [**Descendant combinator**](https://developer.mozilla.org/en-US/docs/Web/CSS/Descendant_combinator)
- `ul > li` - _**Looking inside**_ - Selects **only the direct** `li` elements of `ul`; i.e. it will only select direct children `li` of `ul`; [**Child combinator**](https://developer.mozilla.org/en-US/docs/Web/CSS/Child_combinator)
-  `ul + ul` - _**Looking outside**_ - Selects the `ul` **immediately following** the `ul`; It is not looking inside, but looking outside for the immediately following element; [**Adjacent sibling combinator**](https://developer.mozilla.org/en-US/docs/Web/CSS/Adjacent_sibling_combinator) / [**Next-sibling combinator**](https://www.w3.org/TR/selectors-3/#adjacent-sibling-combinators)
-  `ul ~ ul` - _**Looking outside**_ - Selects **all the following** `ul`'s, but both `ul`'s should be having the same parent; [**General sibling combinator**](https://developer.mozilla.org/en-US/docs/Web/CSS/General_sibling_combinator) / [**Subsequent-sibling combinator**](https://www.w3.org/TR/selectors-3/#general-sibling-combinators)

[^1]: [What does the "~" \(tilde/squiggle/twiddle\) CSS selector mean? \- Stack Overflow](https://stackoverflow.com/questions/10782054/what-does-the-tilde-squiggle-twiddle-css-selector-mean)


## Bootstrap
### col-lg-5 col-xl-4 order-md-3 のようなものを理解する
- グリッドオプション
	- col は幅
	- orderは順序
	- 
| breakpoint |         |
| ---------- | ------- |
| xs         | <576px  |
| sm         | ≥576px  |
| md         | ≥768px  |
| lg         | ≥992px  |
| xl         | ≥1200px |
| xxl        | ≥1400px |

