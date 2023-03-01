# latex-tour

共同作業を快適にするためのlatexの勉強

## 環境構築

### Latexをインストールする

```bash
brew install --cask mactex
```

### VSCodeの拡張機能LaTex Workshopをインストールする

[LaTex Workshop](https://marketplace.visualstudio.com/items?itemName=James-Yu.latex-workshop)をインストールする

### ダウンロードしてきたフォントを使う方法

事前に[googleフォント](https://fonts.google.com/)などからフォントをダウンロードしているとする。

main.texのプリアンブルに次の文を追加することでフォントを追加できる。

```latex
\newfontfamily\newfont[%
    Path = fonts/,
    UprightFont = *-p7PAK,
    Extension = .ttf
    ]{Nkf10MagicumComicumCrassum}
```

\newfont は好きなように変更して良い。この例の場合、ダウンロードしたフォントのパスは、main.texのあるディレクトリから見て

```bash
./fonts/Nkf10MagicumComicumCrassum-p7PAK.ttf
```

となっている。このリポジトリにはfontsディレクトリは無いので、適当に追加してほしい。
使い方はフォントを変更したい文章の先頭に\newfont を加え、全体を{ }で覆うことでスコープできる。

```latex
{\fontname 文章}
```
