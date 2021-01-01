# 如何开始

---
要想使用actix_web首先我们必须引入这个库。

让我们找到Cargo.toml,然后像下面这样修改[dependencies]块
```toml
[dependencies]
actix-web = "3.3.2"
askama = "0.10.5"
askama_actix = "0.11.1"
```
为了能够正常做成web程序我们首先要引入actix-web。

就像之前说的，actix_web是不内置视图引擎的，所以我们还要追加askama来生成页面。

askama_actix是askama为actix_web专门准备的整合库，使用后会让返回页面变得更简单。

这时候如果你执行`cargo build`的话，cargo会下载所有被用到的依赖库。
