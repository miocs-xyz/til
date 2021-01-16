# Rust開発言語

---
## 関連サイト
- [公式サイト](https://www.rust-lang.org)
- [Crates](https://crates.io/)

## インストール
Linuxを使うなら、下記コマンドでRustがインストールできます。
> curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh

## プロジェクトの新規作成
下記コマンドで実行可能のバイナリプロジェクトが作成できます。
> cargo new myproject
>
> あるいは
>
> cargo new myproject --bin

もしただ別のアプリで使えるライブラリを作りたい場合、下記コマンドで作成してください。
> cargo new mylib --lib

##　Rust開発が使えるツール
僕個人はよく下記のツールでRust開発を行っています。
- [Visual Studio Code](https://code.visualstudio.com/)
- [Clion/Intellij](https://www.jetbrains.com/)
  （商用ソフト）

## Rustは何ができる？
もともとRustはシステム開発のために生み出した言語ですが、

個人的にウエブアプリ開発や組み込み開発などでもよく使えると思います。

Rustはローレベル開発言語として基本**なんでもできます**。

まず自分が勉強したいのはRustでのウェブアプリ開発になります。

でもその前にRustの基本をちょっと勉強しないといけません。

**[Rustの基本](Basic)**

[構造体](Basic/rust_struct.ja_jp.ipynb)


- [Web Application](web/README.ja_jp.md)

ビデオ埋め込みテスト
[![Little red ridning hood]()](https://vimeo.com/501149483 "RustでWebアプリケーションを開発する（１）")

