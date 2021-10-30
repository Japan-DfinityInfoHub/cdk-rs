# （非公式） Dfinity ドキュメント翻訳プロジェクト

本リポジトリは、[こちら](https://github.com/Japan-DfinityInfoHub/docs)で実施している Dfinity ドキュメント翻訳プロジェクトの子リポジトリです。

> Dfinity 公式ドキュメントは、[dfinity/docs](https://github.com/dfinity/docs) のリポジトリに全てのドキュメントファイルが集約されているわけではなく、[dfinity/motoko](https://github.com/dfinity/motoko) などの他のリポジトリに置かれた AsciiDoc ファイルが集約されて一つのドキュメントとなっています。

本リポジトリでは、[dfinity/cdk-rs](https://github.com/dfinity/cdk-rs) のドキュメントを翻訳しています。

## 翻訳手順

翻訳の状況は、親リポジトリである Japan-DfinityInfoHub/docs の[翻訳の概要と進捗状況](https://github.com/Japan-DfinityInfoHub/docs/issues/17)の issues を確認してください。

### 手順 1: 翻訳を始める準備の準備

> [Japan-DfinityInfoHub/docs](https://github.com/Japan-DfinityInfoHub/docs) の手順 1 と同じです。
> 既に実施している方は飛ばしてください。

Dfinity のドキュメントは [AsciiDoc](https://azure.microsoft.com/ja-jp/products/visual-studio-code/) によって書かれており、[Antora](https://antora.org/) を用いてビルドされています。
ローカル環境でドキュメントをビルドして確認できるように、以下の手順で Antora をインストールします。

Antora のインストールには [Node](https://nodejs.org/ja/) が必要です。

Windows 10 の場合には [WSL2 上にインストール](https://docs.microsoft.com/ja-jp/windows/dev-environment/javascript/nodejs-on-wsl)することをお勧めします。

Mac OS の場合には [Homebrew でインストール](https://blog.proglus.jp/2004/)するのが良いと思います。

Node のインストールができたら、[Antora のインストール](https://docs.antora.org/antora/2.3/install/install-antora/)を行います。
ここではグローバル環境にインストールする手順を説明します。

```
$ npm i -g @antora/cli@2.3 @antora/site-generator-default@2.3
```

以下のコマンドでインストールできていることを確認します。

```
$ antora -v
```

`2.3.x` などのバージョン名が表示されれば OK です。

### 手順 2: 翻訳を始める準備

まずは、このリポジトリを右上から Fork してください。

そして、リポジトリをクローンします。`your` には、あなたの GitHub のユーザーネームを入れてください。

```
$ git clone https://github.com/your/cdk-rs
$ cd cdk-rs
```

翻訳作業を行うためのブランチを作成します。
どのファイルを翻訳するかは、Japan-DfinityInfoHub/docs の[翻訳の概要と進捗状況](https://github.com/Japan-DfinityInfoHub/docs/issues/17)の翻訳ページ一覧を確認して、翻訳したい箇所をコメントしてください。

ここでは、例として `rust-guide/pages/rust-intro.adoc` を翻訳するためのブランチを作成します。

```
$ git checkout -b rust-guide/pages/rust-intro.adoc
```

これで、翻訳を始める準備は完了です。エディタを使って、翻訳箇所のファイルを編集します。
今回の例の場合、ファイルの場所は、`./docs/modules/` に、上で示した `rust-guide/pages/rust-intro.adoc` を足した、`./docs/modules/rust-guide/pages/rust-intro.adoc` です。

### 手順 3: 翻訳

[スタイルガイド](https://github.com/Japan-DfinityInfoHub/docs/blob/main/styleguide.md)に目を通してください。
わからないことがあれば [Discord](https://discord.gg/ewAxzfTURX) の#ドキュメント翻訳チャネルで質問してください。

エディタとしては [VSCode](https://azure.microsoft.com/ja-jp/products/visual-studio-code/) を推奨します。
[AsciiDoc の拡張機能](https://marketplace.visualstudio.com/items?itemName=asciidoctor.asciidoctor-vscode)を入れると少し幸せになれるかもしれません。

### 手順 4: 翻訳内容の確認

翻訳した文章を確認するために、手順 1 で導入した Antora を用いてローカルビルドします。

```
$ antora local-antora-playbook.yml
```

のコマンドを叩くと、ビルドが実行されます。
ビルド後、`build/site/docs` 以下の html ファイルを直接開きます。

```
$ open build/site/docs/rust-guide/rust-intro.html
```

ブラウザが開き、翻訳が反映されていることが確認できます。

### 手順 5: 翻訳内容のプルリクを出す

翻訳が終わったら、ローカルリポジトリにコミットしたあと、自分のリモートリポジトリにプッシュします。
コミットが複数になった場合、なるべく[１つのコミットにまとめて](https://dev.classmethod.jp/articles/git-rebase-fixup/)いただければありがたいですが、難しければそのままでも OK です。

```
$ git add docs/modules/rust-guide/pages/rust-intro.adoc
$ git commit -m "translated: ust-guide/pages/rust-intro.adoc"
$ git push origin ust-guide/pages/rust-intro.adoc
```

最後に、Github から[プルリクを出します](https://qiita.com/samurai_runner/items/7442521bce2d6ac9330b)。
このとき、出し先が Japan-DfinityInfoHub/cdk-rs になるようにします。
間違えて本家の dfinity/cdk-rs に出してしまわないように気をつけてください。

以上です！メンテナーがレビューをして問題なければマージされます。


# Rust Canister Development Kit

[![Documentation](https://docs.rs/ic-cdk/badge.svg)](https://docs.rs/ic-cdk/)
[![Crates.io](https://img.shields.io/crates/v/ic-cdk.svg)](https://crates.io/crates/ic-cdk)
[![License](https://img.shields.io/crates/l/ic-cdk.svg)](https://github.com/dfinity/cdk-rs/blob/main/src/ic-cdk/LICENSE)
[![Downloads](https://img.shields.io/crates/d/ic-cdk.svg)](https://crates.io/crates/ic-cdk)
[![Test Status](https://github.com/dfinity/cdk-rs/actions/workflows/test.yml/badge.svg)](https://github.com/dfinity/cdk-rs/actions)

**Rust CDK provides tools for building Canisters on Internet Computer (IC).**

You may be looking for:

- [Documentation Site of the Internet Computer](https://smartcontracts.org/)
- [Tutorials of Rust CDK](https://smartcontracts.org/docs/rust-guide/rust-intro.html)
- [Examples](https://github.com/dfinity/cdk-rs/tree/main/examples)
- [`dfx` for managing IC projects](https://github.com/dfinity/sdk)

If you are looking for a crate to communicate with existing canisters on IC,
you may want to check [agent-rs](https://github.com/dfinity/agent-rs).

# Introduction

A `canister` is a WebAssembly (wasm) module that can run on the Internet Computer.

To be a `canister`, a wasm module should communicate with the execution environment using [Canister interfaces (System API)](https://sdk.dfinity.org/docs/interface-spec/index.html#system-api).

This repo provides libraries and tools to facilitate developing canisters in Rust.

- [`ic-cdk`](https://github.com/dfinity/cdk-rs/tree/main/src/ic-cdk):
Bindings of the System API.
- [`ic-cdk-macros`](https://github.com/dfinity/cdk-rs/tree/main/src/ic-cdk-macros):
Annotate functions with attribute macros to make them exposed public interfaces.
- [`ic-cdk-optimizer`](https://github.com/dfinity/cdk-rs/tree/main/src/ic-cdk-optimizer):
A binary tool to reduing size of the compiled wasm module.
- [`ic-certified-map`](https://github.com/dfinity/cdk-rs/tree/main/src/ic-certified-map): An implementation of map which support *certified queries*.

## Rust CDK in Action

In Cargo.toml:

```toml
[lib]
crate-type = ["cdylib"]

[dependencies]
ic-cdk = "0.3"
ic-cdk-macros = "0.3"
```

Then in your rust source code:

```rust
#[ic_cdk_macros::query]
fn print() {
    ic_cdk::print("Hello World from DFINITY!");
}
```

Check [tutorial](https://sdk.dfinity.org/docs/rust-guide/rust-quickstart.html) for a detailed guidance.
