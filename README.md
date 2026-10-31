# horisage（掘り下げ）

音声入力に特化した grill-me / grilling です。Aqua Voice などで思いつくまま長く話すだけで、質問を重ねて考えを詰め、そのまま記事を書くところや実行するところまで進めます。Claude Code と Codex の両方で動きます。

## grill-me / grilling との違い

Matt Pocock さんの [grill-me / grilling](https://github.com/mattpocock/skills) は、質問を 1 問ずつ重ねて考えを詰めるスキルです。キーボードで短く答えるなら、このやり方が合っています。音声入力では一度に長く話せるので、1 問ずつだと往復が増えて疲れます。horisage は同じ考え方を、音声で答える前提で作り直しました。

| | grill-me / grilling | horisage |
|---|---|---|
| 1 回の質問 | 1 問 | 最大 5 問。番号つき |
| 答え方 | 1 問ずつ答える | 番号なしで、まとめて話せばよい |
| 推奨の答え | すべての問いに付ける | 決めごとだけに付ける。体験や気持ちの問いには付けない |
| 話し言葉 | 想定していない | 言い直し・先回りの答え・脱線を仕分け、誤変換を直す |
| 記録 | grill-me は残さない。grill-with-docs は用語集と ADR に残す | 取材メモに、本人の発言・AI の解釈・調べた事実を分けて残す |
| 終わり | 考えが詰まったら終わる | 記事を書くか、計画を立てて実行する |
| 再開 | なし | 「続きから」で戻れる |

20 問かかる話なら、grill-me では 20 往復、horisage では 4〜5 往復で済みます。

## 音声向けの工夫

- **言い直しに強い**: 「いや、違くて」「やっぱり」のあとの答えを採ります。
- **誤変換を直す**: 文脈で明らかなものは黙って直し、固有名詞と数字だけ 1 回確かめます。何度も誤変換された語は、最後に音声入力の辞書に足す候補として挙げます。
- **誘導しない**: 体験や気持ちを聞く問いに推奨を付けないので、記事が AI の言葉ではなく本人の言葉になります。
- **画面を見なくてよい**: 表や長いコードを出さず、声で聞いても分かる短い文で返します。
- **離席しても止まらない**: commit・push・公開などの判断と許可を計画の段階でまとめて取り、そのあとは最後まで進めます。
- **メモは git に入らない**: 取材メモは `.horisage/` に置き、コミットされないようにします。

## 流れ

1. **掘り下げ**: 質問のラリーで、目的・相手・主張・範囲・根拠・制約を決めていきます。
2. **まとめ**: 取材メモの要点を見せ、理解が合っているかを 1 回だけ確かめます。
3. **計画と実行**: 記事なら構成を見出しで見せてから書きます。それ以外なら `plan.md` を作り、合意した範囲で最後まで進めて報告します。

## 使い方

次のように話しかけます。

```
掘り下げて。いま考えているのは……（思いつくまま長く話す）
聞き取って記事にして
壁打ちして / ドリルダウンして / 話すから整理して
続きから
```

Claude Code では `/horisage` でも始められます。

答えるときのコツです。

- 番号を言わなくても大丈夫です。思いついた順に、まとめて話してください。
- 「全部はい」「2 以外はい」「3 番はパス」で推奨を受け入れたり飛ばしたりできます。
- 「まとめて」「書いて」と言えば、いつでも掘り下げを切り上げられます。

## 入れ方

### Claude Code（リポジトリ単位）

```sh
claude plugin marketplace add heyk1njo/horisage --scope project
claude plugin install horisage@horisage -s project
```

スキルに加えて、事実を調べる `researcher` と、成果物を取材メモと照らす `reviewer` の 2 つのエージェントが入ります。

### Codex

```sh
codex plugin marketplace add heyk1njo/horisage
codex plugin add horisage@horisage
```

Codex のプラグインは `~/.codex` に入るので、すべてのリポジトリで使えるようになります。

### スキルだけをリポジトリに入れる

```sh
npx skills add heyk1njo/horisage -a claude-code -a codex
```

この方法ではエージェントは入りません。horisage は、エージェントがなければ自分で調べて照合します。

## ファイル

```
skills/horisage/
  SKILL.md                    掘り下げの本体
  references/notes-template.md 取材メモの形
  references/plan.md          計画と合意
  references/run.md           実行と報告
  references/write.md         記事を書く
agents/
  researcher.md               事実を調べる（Claude Code）
  reviewer.md                 取材メモと照らす（Claude Code）
```

## クレジット

質問を重ねて設計を詰めるやり方は、Matt Pocock さんの [mattpocock/skills](https://github.com/mattpocock/skills)（MIT License）の grill-me と grilling を参考にしました。

## ライセンス

[MIT](LICENSE)
