# ollamaを使ってみた

## 検証環境
- ローカル環境
  - 端末
    - Windows
  - ollama
    - ollama 0.2.8
  - LLM
    - llama3
    - llama3.1
    - phi3

## セットアップ
https://ollama.com

ollama公式HPからダウンロードし、インストール  
アプリケーションを開くと、ステータスメニューバーにラマのアイコンが表示され```ollama```が使えるようになる

```
% ollama --version
ollama version is 0.2.8
```

# 使い方
## 1. テキスト生成モデル
### 代表的なテキスト生成モデル
- [gemma](https://ollama.com/library/gemma)
  - Google社が公開しているGeminiをもとに設計されたLLM
- [llama3](https://ollama.com/library/llama3)
  - Meta社が公開している小型かつ高性能なLLM
- [phi3](https://ollama.com/library/phi3)
  - Microsoft社による大規模言語モデル(LLM)ならぬ小規模言語モデル(SLM)
- [CommandR+](https://ollama.com/library/command-r-plus)
  - カナダのスタートアップ企業、Cohere社による、RAGとToolの使用などの長いコンテキストの処理に最適化したモデル
- [mistral](https://ollama.com/library/mistral)
  - フランスのスタートアップ企業、Mistral社による、パフォーマンスと使いやすさを追記有したモデル
- [mixtral](https://ollama.com/library/mixtral)
  - 同じくMistral社による混合エキスパートモデル


### テキスト生成モデルの使い方

使いたいLLMモデルを指定し```pull```することで、モデルファイルがダウンロードされ、準備が整います。
```
% ollama pull [モデル名]
pulling manifest
pulling 109037bec39c... 100%  ██████████████████████████▏ 8.4 KB
pulling 109037bec39c... 100% ▕█████████████████████████████████████████████████████████▏  136 B
pulling 65bb16cf5983... 100% ▕█████████████████████████████████████████████████████████▏  109 B
pulling 0c2a5137eb3c... 100% ▕█████████████████████████████████████████████████████████▏  483 B
verifying sha256 digest
writing manifest
removing any unused layers  
success
```

ダウンロードしたモデルを確認する方法
```
% ollama list
gemma:latest    a72c7f4d0a15    5.0 GB  48 minutes ago
llama3.1:latest 62757c860e01    4.7 GB  3 days ago
phi3:latest     d184c916657e    2.2 GB  4 days ago
llama3:latest   365c0bd3c000    4.7 GB  4 days ago
```

不要なモデルを削除する方法
```
ollama remove [モデル名]
```

```run```コマンドでLLMを立ち上げると会話モードに入り
```
% ollama run [モデル名]
>>> Send a message (/? for help)
```
メッセージを送信できるようになります。
```
>>>　こんにちは
こんにちは！元気ですか？
今日はどのようなことでしょうか？何か教えてください。

>>> Send a message(/? for help)
```
メッセージを送信すると返答が表示され、チャット形式で会話できます。
```
% ollama run [モデル名]
>>> こんにちは
こんにちは！元気ですか？
今日はどのようなことでしょうか？何か教えてください。

>>> /bye
```
```/bye```で会話モードが終了します。
最初の```run```時に引数でメッセージを渡すことで、1回のコマンドで１往復のチャットを実行することも可能です。
```
% ollama run [モデル名] こんにちは
こんにちは！元気ですか？
今日はどのようなことでしょうか？何か教えてください。
```
