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
% ollama pull llama3
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

```run```コマンドでLLMを立ち上げると会話モードに入り
```
% ollama run gemma
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
% ollama run gemma
>>> こんにちは
こんにちは！元気ですか？
今日はどのようなことでしょうか？何か教えてください。

>>> /bye
```
```/bye```で会話モードが終了します。
最初の```run```時に引数でメッセージを渡すことで、1回のコマンドで１往復のチャットを実行することも可能です。
```
% ollama run gemma こんにちは
こんにちは！元気ですか？
今日はどのようなことでしょうか？何か教えてください。
```
