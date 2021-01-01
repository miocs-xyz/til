# Rustよりウエブアプリケーションの作成

---
## フレームワーク
今流行ってるRustのフレームワークが多いです。いろいろ比べて見た結果Acitx_Webを選びました。
- [actix_web](https://actix.rs/)
残念ながらactixにはビューエンジンが組み込んでいないため、そっちのほうはaskamaを使いたいと思います。
- [askama](https://github.com/djc/askama)

じゃこれから、Rust及び上記のフレームワークを使って簡単なCMSシステムを作ろうとします。このプロジェクトによってRustがウエブアプリケーション開発
に向いてるかどうかを検証したいと思います。

**このプロジェクトのソースは下記に公開されております。**
- [iciclog](https://bitbucket.org/miocs-xyz/iciclog/src/main/)