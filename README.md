# ai-company-os

**人がいなくても回る組織のためのOS**
*An OS for an organization that keeps doing useful work without people.*

![ai-company-os の組織図](docs/org.png)

## 考え方 / The idea

- **価値を決めるのは外。** 仕事は、社会・利用者・コミュニティの役に立って初めて成立する。
- **設計の順番：** 成果 → 検収 → 成果物を作る人（エージェント）。
- **各層は1つだけ：** 秘書AI 1つ、部長AI 1つ。部長は増やさない。
- **部下は横並びで、終われば消える。** 学びは消える前に記録へ書き戻す。
- **人間の役割は段階的に小さくする：** CEO → Owner → Auditor。緊急停止と法的な所有は最後まで人間に残す。

## OSとしての対応 / Mapping

| OS | ai-company-os |
|---|---|
| カーネル / kernel | 部長AI（MD）：記憶・検収基準・判断のしきい値 |
| プロセス / process | 部下AI（worker）：案件ごとに起動し、終われば消える |
| ファイルシステム / filesystem | `tasks/*.md`：タスクと学びの正本 |
| シェル・入出力 / shell, I/O | 秘書AI（secretary）：外との窓口 |
| 権限 / permissions | しきい値：ACCEPT / WARN / ESCALATE / BLOCK |
| アプリ / apps | 各プロジェクト |

## 構成 / Layout

```text
secretary/   秘書AIの役割定義
md/          部長AIの役割・検収基準・判断のしきい値
workers/     部下AIのテンプレート
tasks/       タスクをMarkdownファイルで管理する（正本）
docs/        図・設計メモ
```

## 状態 / Status

構想段階です。まず1つのプロジェクトで試し、うまくいけば他へ広げます。
*Early concept. It will be piloted on one project first.*
