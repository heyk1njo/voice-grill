# horisage（掘り下げ）

音声入力で話しながら考えを掘り下げ、計画して実行するまで進める Claude Code / Codex 用のスキルです。Aqua Voice などで長く話した内容をまとめて受け止め、番号つきの質問を最大 5 問ずつ重ねて考えを明確にします。まとめに合意したら、計画を立てて実行するか、取材メモだけを材料に記事を書きます。

[grill-me / grilling](https://github.com/mattpocock/skills) の「質問を重ねて考えを詰める」やり方を、音声入力向けに作り替えました。

## 何が違うか

- **まとめて聞いて、まとめて答える**: grilling は 1 問ずつ聞きます。音声なら一度に長く話せるので、horisage は 1 ラウンドに最大 5 問を出し、番号なしの長い回答から答えを仕分けます。合計 5〜30 問、ラリーが 10〜20 往復になっても構いません。
- **話し言葉に強い**: 言い直しは後のほうを採ります。誤変換は文脈で直し、固有名詞や数字だけ 1 回確かめます。何度も誤変換された語は、最後に音声入力の辞書に足す候補として挙げます。
- **誘導しない**: 範囲や方針などの決めごとには推奨の答えを付け、「はい」で受け入れられます。体験や気持ちを聞く問いには推奨を付けません。
- **取材メモに残す**: 本人の発言、AI の解釈、調べた事実を分けて `.horisage/` に書きます。このフォルダは git に入らないようにします。途中で止めても「続きから」で再開できます。
- **実行まで進む**: 判断と許可（commit・push・公開など）を計画の段階でまとめて取るので、離席している間も止まらずに進めます。

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
