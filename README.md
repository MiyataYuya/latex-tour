# latex-tour
共同作業を快適にするためのlatexの勉強

// editor.wordSeparators: 単語単位での移動を行う場合の区切り文字を指定
  // 日本語文書で単語移動を使うため、助詞や読点、括弧を区切り文字として指定する
  "editor.wordSeparators": "./\\()\"'-:,.;<>~!@#$%^&*|+=[]{}`~?　、。「」【】『』（）！？てにをはがのともへでや",
  // 設定: LaTeX Workshop
  // LaTeX Workshop ではビルド設定を「Tool」と「Recipe」という2つで考える
  //   Tool: 実行される1つのコマンド。コマンド (command) と引数 (args) で構成される
  //   Recipe: Tool の組み合わわせを定義する。Tool の組み合わせ (tools) で構成される。
  //           tools の中で利用される Tool は "latex-workshop.latex.tools" で定義されている必要がある。
  // latex-workshop.latex.tools: Tool の定義
  "latex-workshop.latex.tools": [
    {
      "name": "latexmk",
      "command": "latexmk",
      "args": [
        "-synctex=1",
        "-interaction=nonstopmode",
        "-file-line-error",
        "-pdf",
        "%DOC%"
      ]
    },
    // latexmk を利用した xelatex によるビルドコマンド
    {
      "name": "Latexmk (XeLaTeX)",
      "command": "latexmk",
      "args": [
        "-f",
        "-gg",
        "-pv",
        "-xelatex",
        "-synctex=1",
        "-interaction=nonstopmode",
        "-file-line-error",
        "%DOC%"
      ]
    },
    // latexmk を利用した uplatex によるビルドコマンド
    {
      "name": "Latexmk (upLaTeX)",
      "command": "latexmk",
      "args": [
        "-f",
        "-gg",
        "-pv",
        "-synctex=1",
        "-interaction=nonstopmode",
        "-file-line-error",
        "%DOC%"
      ]
    },
    // latexmk を利用した platex によるビルドコマンド
    // 古い LaTeX のテンプレートを使いまわしている (ドキュメントクラスが jreport や jsreport ) 場合のため
    {
      "name": "Latexmk (pLaTeX)",
      "command": "latexmk",
      "args": [
        "-f",
        "-gg",
        "-pv",
        "-latex='platex'",
        "-latexoption='-kanji=utf8 -no-guess-input-env'",
        "-synctex=1",
        "-interaction=nonstopmode",
        "-file-line-error",
        "%DOC%"
      ]
    },
    // latexmk を利用した lualatex によるビルドコマンド
    {
      "name": "Latexmk (LuaLaTeX)",
      "command": "latexmk",
      "args": [
        "-f",
        "-gg",
        "-pv",
        "-lualatex",
        "-synctex=1",
        "-interaction=nonstopmode",
        "-file-line-error",
        "%DOC%"
      ]
    }
  ],
  // latex-workshop.latex.recipes: Recipe の定義
  "latex-workshop.latex.recipes": [
    {
      "name": "latexmk",
      "tools": [
        "latexmk"
      ]
    },
    // XeLaTeX で書かれた文書のビルドレシピ
    {
      "name": "XeLaTeX",
      "tools": [
        "Latexmk (XeLaTeX)"
      ]
    },
    // LaTeX(upLaTeX) で書かれた文書のビルドレシピ
    {
      "name": "upLaTeX",
      "tools": [
        "Latexmk (upLaTeX)"
      ]
    },
    // LaTeX(pLaTeX) で書かれた文書のビルドレシピ
    {
      "name": "pLaTeX",
      "tools": [
        "Latexmk (pLaTeX)"
      ]
    },
    // LuaLaTeX で書かれた文書のビルドレシピ
    {
      "name": "LuaLaTeX",
      "tools": [
        "Latexmk (LuaLaTeX)"
      ]
    }
  ],
  // latex-workshop.latex.magic.args: マジックコメント付きの LaTeX ドキュメントをビルドする設定
  // '%!TEX' で始まる行はマジックコメントと呼ばれ、LaTeX のビルド時にビルドプログラムに解釈され、
  // プログラムの挙動を制御する事ができる。
  // 参考リンク: https://blog.miz-ar.info/2016/11/magic-comments-in-tex/
  "latex-workshop.latex.magic.args": [
    "-f",
    "-gg",
    "-pv",
    "-synctex=1",
    "-interaction=nonstopmode",
    "-file-line-error",
    "%DOC%"
  ],
  // latex-workshop.latex.clean.fileTypes: クリーンアップ時に削除されるファイルの拡張子
  // LaTeX 文書はビルド時に一時ファイルとしていくつかのファイルを生成するが、最終的に必要となるのは
  // PDF ファイルのみである場合などが多い。また、LaTeX のビルド時に失敗した場合、失敗時に生成された
  // 一時ファイルの影響で、修正後のビルドに失敗してしまう事がよくある。そのため、一時的なファイルを
  // 削除する機能 (クリーンアップ) が LaTeX Workshop には備わっている。
  "latex-workshop.latex.clean.fileTypes": [
    "*.aux",
    "*.bbl",
    "*.blg",
    "*.idx",
    "*.ind",
    "*.lof",
    "*.lot",
    "*.out",
    "*.toc",
    "*.acn",
    "*.acr",
    "*.alg",
    "*.glg",
    "*.glo",
    "*.gls",
    "*.ist",
    "*.fls",
    "*.log",
    "*.fdb_latexmk",
    "*.synctex.gz",
    // for Beamer files
    "_minted*",
    "*.nav",
    "*.snm",
    "*.vrb",
  ],
  // latex-workshop.view.pdf.viewer: PDF ビューアの開き方
  // VSCode 自体には PDF ファイルを閲覧する機能が備わっていないが、
  // LaTeX Workshop にはその機能が備わっている。
  // "tab" オプションを指定すると、今開いているエディタを左右に分割し、右側に生成されたPDFを表示するようにしてくれる
  // この PDF ビュアーは LaTeX のビルドによって更新されると同期して内容を更新してくれる。
  "latex-workshop.view.pdf.viewer": "browser",
  "latex-workshop.latex.autoClean.run": "onFailed",
  "latex-workshop.latex.autoBuild.run": "never",
  "julia.enableTelemetry": true,
  "julia.enableCrashReporter": true,