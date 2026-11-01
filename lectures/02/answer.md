# 第2回 解答

## 演習

- 使ったモデル・設定（`result.json` の `config` から）：
  　"base_model": "Qwen/Qwen3.5-0.8B",
    "revision": "2fc06364715b967f1860aea9cf38778875588b17",
    "seed": 42,
    "num_train_epochs": 20,
    "warmup_steps": 6,
    "lr": 0.0002,
    "lora_r": 16,
    "lora_alpha": 32,
    "max_seq_len": 512,
    "max_new_tokens": 96,
    "gen": {
      "do_sample": false｝
- 自分で学習を実行したか（`executed_training_myself`）：はい
- 学習前：`format_rate` = 0.09523809523809523　 / `content_rate` =　0.0
- 学習後：`format_rate` =　1.0 / `content_rate` = 0.9047619047619048
- 退行した質問：成績はいつ出ますか、オフィスアワーは事前予約が必要ですか
- 学習後に残った失敗と、その型（根拠なしの質問に断定した / 根拠ありの質問に確認要求で逃げた / 形式の崩れ）：根拠なしの質問に断定した
- 知識を問う質問（セクション 6）の結果（学習前の分類 → 学習後の分類）と気づいたこと：学習前の分類はすべて「format_error」であったが、学習後は「担当教員の名前は何ですか」と「次回の講義のテーマは何ですか」の質問に対して、わからないと返答できるようになっていた。
- 学習で変わったこと・変わらなかったこと：学習することで、同じ回答形式で回答を作成するようになった。

## 宿題

- 取り組んだレベル：基礎
- 変えた設定やデータ： "lora_r"を16→32に変更
- 結果（比較表や数字）："lora_r"を16から32に変更しても、"format_rate": 1.0, "content_rate": 0.9047619047619048,と正答率に影響しなかった。一方、"seconds"は 43.6から44.8に伸びた。

###既定値での実行結果
{
  "config": {
    "base_model": "Qwen/Qwen3.5-0.8B",
    "revision": "2fc06364715b967f1860aea9cf38778875588b17",
    "seed": 42,
    "num_train_epochs": 20,
    "warmup_steps": 6,
    "lr": 0.0002,
    "lora_r": 16,
    "lora_alpha": 32,
    "max_seq_len": 512,
    "max_new_tokens": 96,
    "gen": {
      "do_sample": false
    }
  },
  "versions": {
    "transformers": "5.21.0",
    "peft": "0.21.2",
    "trl": "1.14.2",
    "torch": "2.11.0+cu130"
  },
  "method": "LoRA（量子化なし）",
  "before": {
    "label": "before",
    "n": 21,
    "format_rate": 0.09523809523809523,
    "content_rate": 0.0,
    "both_rate": 0.0,
    "seconds": 21.9
  },
  "after": {
    "label": "after",
    "n": 21,
    "format_rate": 1.0,
    "content_rate": 0.9047619047619048,
    "both_rate": 0.9047619047619048,
    "seconds": 43.6
  },
  "regressed": [],
  "executed_training_myself": true
}

###"lora_r"を16→32に変更後の結果
{
  "config": {
    "base_model": "Qwen/Qwen3.5-0.8B",
    "revision": "2fc06364715b967f1860aea9cf38778875588b17",
    "seed": 42,
    "num_train_epochs": 20,
    "warmup_steps": 6,
    "lr": 0.0002,
    "lora_r": 32,
    "lora_alpha": 32,
    "max_seq_len": 512,
    "max_new_tokens": 96,
    "gen": {
      "do_sample": false
    }
  },
  "versions": {
    "transformers": "5.18.0",
    "peft": "0.21.1",
    "trl": "1.14.2",
    "torch": "2.11.0+cu130"
  },
  "method": "LoRA（量子化なし）",
  "before": {
    "label": "before",
    "n": 21,
    "format_rate": 0.09523809523809523,
    "content_rate": 0.0,
    "both_rate": 0.0,
    "seconds": 31.2
  },
  "after": {
    "label": "after",
    "n": 21,
    "format_rate": 1.0,
    "content_rate": 0.9047619047619048,
    "both_rate": 0.9047619047619048,
    "seconds": 44.8
  },
  "regressed": [],
  "executed_training_myself": true
}
