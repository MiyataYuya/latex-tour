# latex-tour

共同作業を快適にするためのlatexの勉強

## 環境構築

### Latexをインストールする

```shell
brew install --cask mactex
```

### VSCodeの拡張機能LaTex Workshopをインストールする

[LaTex Workshop](https://marketplace.visualstudio.com/items?itemName=James-Yu.latex-workshop)をインストールする


### インターネットからダウンロードしてきたフォントを使う方法。

[googleフォント](https://fonts.google.com/)などからフォントをダウンロードしているとする。

main.tex と同じディレクトリにダウンロードしたフォント(fontA.otf)を追加し、main.texのプリアンブルに次の文を追加する。
```
\font\fontname=[fontA.otf]
```
ここで、[ ]内はmain.tex からみたフォントへの相対パスであり、\fontnameは好きに決めて良い。フォントを複数使いたい場合は、適当なディレクトリ(ex. fonts/)を作ってそこにフォントを配置し、[ ]内は./fonts/fontA.otfのようにすれば良い。

本文中では
```
{\fontname 本文}
```
のようにして使用する。
