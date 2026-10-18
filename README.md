# content-ops

Kho nội dung cho dnhnam.com và Fanpage Facebook, vận hành bằng Claude Code cloud session.

## Cấu trúc

| Thư mục / file | Dùng để |
|---|---|
| `CLAUDE.md` | Hướng dẫn cố định cho Claude, tự động đọc ở đầu mỗi session |
| `STYLE.md` | Giọng văn blog và Fanpage, kèm checklist |
| `briefs/` | Đầu vào do Nam viết. Mẫu: `briefs/_template.md` |
| `drafts/` | Bài blog nháp |
| `social/` | Post Facebook |
| `published/` | Bài đã đăng |

## Quy trình một bài

1. Copy `briefs/_template.md` thành `briefs/<slug>.md`, điền đủ phần **Trải nghiệm thật**.
2. Commit brief lên GitHub.
3. Vào [claude.ai/code](https://claude.ai/code), chọn repo này, giao task (prompt mẫu bên dưới).
4. Mở diff, comment từng dòng, gửi để Claude sửa. Lặp lại tới khi ổn.
5. Bấm **Create PR**, merge vào `main`.
6. Đăng bài, rồi giao Claude chuyển file sang `published/` và điền URL.

## Prompt mẫu

**Viết bài từ brief**

```
Đọc STYLE.md và briefs/cloud-session-cho-content-ops.md.
Viết bài blog vào drafts/ theo đúng frontmatter trong CLAUDE.md.
Chạy checklist cuối STYLE.md trước khi báo xong.
```

**Sửa sau khi đã điền [NAM: ...]**

```
Tôi đã điền các chỗ [NAM: ...] trong drafts/<slug>.md.
Đọc lại toàn bài, làm mượt các đoạn vừa điền cho khớp nhịp văn xung quanh.
Không thêm ý mới.
```

**Tách post Facebook**

```
Từ drafts/<slug>.md, tách 3 post Facebook vào social/ theo Phần 2 của STYLE.md.
Mỗi post một ý khác nhau. Ghi COMMENT ĐẦU kèm placeholder link bài gốc.
```

**Rà soát toàn kho (hợp làm routine hàng tuần)**

```
Rà tất cả file trong drafts/. Liệt kê bài nào còn [NAM: ...] chưa điền,
bài nào vi phạm danh sách cấm trong STYLE.md, và bài nào status: ready
nhưng chưa có meta_description. Không sửa file, chỉ báo cáo.
```

## Mẹo

- Lần đầu chọn chế độ **Plan** để xem Claude định làm gì. Quen rồi chuyển **Accept edits**.
- Brief càng nhiều chi tiết thật, bài càng ít chỗ `[NAM: ...]`.
- Mỗi bài một session, một branch. Có thể chạy song song nhiều bài.
