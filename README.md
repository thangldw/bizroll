# BizRoll Production Artifact

Generated static files for the [BizRoll production website](https://thangldw.github.io/bizroll/).

[English](#english) · [Tiếng Việt](#tiếng-việt) · [日本語](#日本語)

> This is a deployment repository. Application source changes belong in [`thangldw/bizroll-game`](https://github.com/thangldw/bizroll-game).

---

## English

### Purpose

This repository is the GitHub Pages publication target for BizRoll. It contains the generated output of the source repository's `dist/` directory and is served at <https://thangldw.github.io/bizroll/>.

Do not use this repository for application development. Source code, tests, Supabase migrations, Edge Functions, environment templates, and release automation are maintained in [`thangldw/bizroll-game`](https://github.com/thangldw/bizroll-game).

### Repository contents

| Path | Purpose | Edit manually? |
| --- | --- | --- |
| `index.html` | Production application entry point | No |
| `assets/` | Hashed JavaScript, CSS, fonts, and images | No |
| `favicon.svg` | Generated site icon | No |
| `.nojekyll` | Disables Jekyll processing on GitHub Pages | No |
| `README.md` | Deployment-repository documentation | Yes |
| `.gitignore` | Repository-specific ignore rules | Yes |

Hashed filenames are expected to change between releases. Never patch generated JavaScript or CSS directly: the change will be lost on the next deployment and cannot be validated from source.

### Release procedure

From a clean checkout of `bizroll-game`:

```bash
npm ci
npm run release:check
```

After the gate passes:

1. Replace the generated contents of this repository with the exact contents of `bizroll-game/dist/`.
2. Preserve `.git/`, `.gitignore`, and this `README.md`.
3. Review all additions, modifications, and deletions. Generated files must not include `.env` files, source maps, TypeScript source, database dumps, or privileged credentials.
4. Record the source commit SHA in the release change, commit, and push the artifact.
5. Wait for GitHub Pages to complete, then run from the source repository:

```bash
npm run test:e2e:prod
```

6. Verify the production URL in a fresh browser session.

The full deployment, backup, rollback, and incident procedures are documented in the source repository's [operations runbook](https://github.com/thangldw/bizroll-game/blob/main/OPERATIONS.md).

### Rollback

Restore the last known-good artifact commit, push it, wait for GitHub Pages, and rerun the production smoke test. A web rollback does not roll back Supabase migrations or the `match-action` Edge Function; confirm backend compatibility before restoring an older client.

### Security

- Do not commit secrets, database exports, real environment files, or source maps.
- A Supabase publishable/anonymous key may be present in the client bundle by design; privileged service-role keys and database credentials must never be present.
- Report suspected vulnerabilities privately to the repository owner rather than posting exploitable details publicly.

No open-source license is currently included. All rights are reserved unless the repository owner states otherwise.

---

## Tiếng Việt

### Mục đích

Repo này là đích phát hành GitHub Pages của BizRoll. Repo chứa output đã sinh từ thư mục `dist/` của source repo và được phục vụ tại <https://thangldw.github.io/bizroll/>.

Không dùng repo này để phát triển ứng dụng. Source code, test, Supabase migration, Edge Function, template môi trường và công cụ release được duy trì tại [`thangldw/bizroll-game`](https://github.com/thangldw/bizroll-game).

### Nội dung repo

| Đường dẫn | Mục đích | Sửa thủ công? |
| --- | --- | --- |
| `index.html` | Entry point của ứng dụng production | Không |
| `assets/` | JavaScript, CSS, font và hình ảnh có tên hash | Không |
| `favicon.svg` | Icon website đã sinh | Không |
| `.nojekyll` | Tắt xử lý Jekyll trên GitHub Pages | Không |
| `README.md` | Tài liệu của repo deployment | Có |
| `.gitignore` | Quy tắc ignore riêng của repo | Có |

Tên file có hash sẽ thay đổi giữa các bản release. Không patch trực tiếp JavaScript hoặc CSS đã sinh: thay đổi sẽ mất ở lần deploy sau và không thể được kiểm tra từ source.

### Quy trình phát hành

Từ checkout sạch của `bizroll-game`:

```bash
npm ci
npm run release:check
```

Sau khi gate đạt:

1. Thay toàn bộ nội dung đã sinh của repo này bằng nội dung chính xác từ `bizroll-game/dist/`.
2. Giữ lại `.git/`, `.gitignore` và `README.md` này.
3. Review mọi file thêm, sửa và xóa. File đã sinh không được chứa `.env`, source map, TypeScript source, database dump hay credential đặc quyền.
4. Ghi source commit SHA trong thay đổi phát hành, commit và push artifact.
5. Chờ GitHub Pages hoàn tất, sau đó chạy từ source repo:

```bash
npm run test:e2e:prod
```

6. Kiểm tra URL production trong một phiên trình duyệt mới.

Quy trình đầy đủ về deploy, backup, rollback và xử lý sự cố nằm trong [operations runbook](https://github.com/thangldw/bizroll-game/blob/main/OPERATIONS.md) của source repo.

### Rollback

Khôi phục artifact commit tốt gần nhất, push, chờ GitHub Pages và chạy lại production smoke test. Rollback web không rollback Supabase migration hoặc Edge Function `match-action`; phải xác nhận tương thích backend trước khi phục hồi client cũ.

### Bảo mật

- Không commit secret, database export, file môi trường thật hoặc source map.
- Supabase publishable/anonymous key có thể xuất hiện trong client bundle theo thiết kế; service-role key đặc quyền và database credential tuyệt đối không được xuất hiện.
- Báo cáo lỗ hổng riêng cho chủ repo, không đăng chi tiết có thể khai thác công khai.

Hiện chưa có giấy phép nguồn mở. Mọi quyền được bảo lưu trừ khi chủ repo công bố khác.

---

## 日本語

### 目的

このリポジトリは BizRoll の GitHub Pages 公開先です。Source Repository の `dist/` から生成された出力を格納し、<https://thangldw.github.io/bizroll/> で配信します。

このリポジトリでアプリケーション開発を行わないでください。Source Code、Test、Supabase Migration、Edge Function、環境 Template、Release Automation は [`thangldw/bizroll-game`](https://github.com/thangldw/bizroll-game) で管理されています。

### リポジトリ内容

| Path | 用途 | 直接編集? |
| --- | --- | --- |
| `index.html` | 本番アプリケーションの Entry Point | いいえ |
| `assets/` | Hash 付き JavaScript、CSS、Font、Image | いいえ |
| `favicon.svg` | 生成済み Site Icon | いいえ |
| `.nojekyll` | GitHub Pages の Jekyll 処理を無効化 | いいえ |
| `README.md` | Deployment Repository の文書 | はい |
| `.gitignore` | リポジトリ固有の Ignore Rule | はい |

Hash 付きファイル名はリリースごとに変更されます。生成済み JavaScript や CSS を直接修正しないでください。次のデプロイで失われ、Source から検証できない変更になります。

### リリース手順

`bizroll-game` の clean な Checkout で実行します。

```bash
npm ci
npm run release:check
```

Gate 成功後:

1. このリポジトリの生成コンテンツを `bizroll-game/dist/` の正確な内容で置換します。
2. `.git/`、`.gitignore`、この `README.md` を保持します。
3. 追加・変更・削除をすべてレビューします。生成ファイルに `.env`、Source Map、TypeScript Source、Database Dump、特権認証情報を含めてはいけません。
4. リリース変更に source commit SHA を記録し、Artifact を Commit/Push します。
5. GitHub Pages の完了を待ち、Source Repository から次を実行します。

```bash
npm run test:e2e:prod
```

6. 新しいブラウザセッションで本番 URL を確認します。

Deployment、Backup、Rollback、Incident 対応の詳細は Source Repository の [Operations Runbook](https://github.com/thangldw/bizroll-game/blob/main/OPERATIONS.md) を参照してください。

### ロールバック

直近の正常な Artifact Commit を復元して Push し、GitHub Pages 完了後に本番 Smoke Test を再実行します。Web の Rollback は Supabase Migration や `match-action` Edge Function を戻しません。古い Client を復元する前に Backend 互換性を確認してください。

### セキュリティ

- Secret、Database Export、実際の環境ファイル、Source Map をコミットしないでください。
- Supabase publishable/anonymous key は設計上 Client Bundle に含まれることがありますが、特権 service-role key と Database Credential は絶対に含めてはいけません。
- 脆弱性の疑いはリポジトリ所有者へ非公開で報告し、悪用可能な詳細を公開しないでください。

現在、オープンソースライセンスは含まれていません。リポジトリ所有者が別途明示しない限り、すべての権利は留保されています。
