# CLAUDE.md — content-ops

Hướng dẫn cố định cho Claude. Đọc file này ở đầu mỗi session, trước khi làm bất cứ việc gì.

## Repo này là gì

Kho nội dung của Nam (dnhnam.com và Fanpage Facebook). Repo chứa brief, bài nháp, post mạng xã hội và bài đã đăng, toàn bộ ở dạng Markdown. Không có code chạy production ở đây.

Người dùng repo: Nam, làm marketing và bán hàng. Trao đổi bằng tiếng Việt.

## Cấu trúc thư mục

```
briefs/       Đầu vào: chủ đề, từ khóa, trải nghiệm thật của Nam. Claude chỉ đọc, không sửa.
drafts/       Bài blog nháp do Claude viết từ brief.
social/       Post Facebook tách ra từ bài blog hoặc từ brief.
published/    Bài đã đăng. Chỉ di chuyển file vào đây khi Nam yêu cầu rõ.
STYLE.md      Quy tắc giọng văn. Bắt buộc đọc trước khi viết bất cứ nội dung nào.
```

## Quy trình

1. Nam tạo brief trong `briefs/` theo mẫu `briefs/_template.md`.
2. Claude đọc `STYLE.md` và brief, viết bài vào `drafts/`.
3. Nam review diff, comment từng dòng, Claude sửa.
4. Khi bài ổn, Claude tách 3 post Facebook vào `social/` nếu Nam yêu cầu.
5. Sau khi đăng, Nam yêu cầu chuyển bài sang `published/` và điền URL vào frontmatter.

## Đặt tên file

- Dùng slug không dấu, chữ thường, nối bằng gạch ngang: `drafts/cloud-session-cho-content-ops.md`.
- File trong `drafts/` và `published/` dùng đúng slug của brief tương ứng.
- Post Facebook: `social/<slug>-fb-1.md`, `social/<slug>-fb-2.md`, `social/<slug>-fb-3.md`.

## Frontmatter cho bài blog

Mỗi file trong `drafts/` mở đầu bằng:

```yaml
---
title: "Tiêu đề bài"
slug: slug-khong-dau
keyword: từ khóa chính
meta_description: "Dưới 155 ký tự, nêu lợi ích hoặc tình huống"
brief: briefs/<slug>.md
status: draft        # draft | review | ready | published
word_count: 0
published_url: ""
---
```

Cập nhật `word_count` sau mỗi lần sửa.

## Quy tắc bắt buộc

- **Giọng văn:** làm đúng `STYLE.md`. Chạy checklist cuối file đó trước khi báo xong.
- **Trung thực:** chỉ dùng trải nghiệm, con số, câu chuyện có trong brief. Không bịa trải nghiệm cá nhân của Nam. Thiếu thì chèn `[NAM: thêm ví dụ thật về ...]` để Nam điền.
- **Không sửa `briefs/`** trừ khi Nam yêu cầu rõ.
- **Không đụng `published/`** trừ khi Nam yêu cầu rõ.
- **Một task, một bài.** Không viết nhiều bài trong cùng một branch trừ khi được yêu cầu.
- **Không tự thêm số liệu thị trường** hay trích dẫn nguồn ngoài nếu brief không cung cấp. Nếu cần, ghi `[NAM: cần số liệu về ...]`.

## Khi báo xong một task

Trả lời ngắn, gồm:

1. File đã tạo hoặc sửa.
2. Số chữ.
3. Danh sách các chỗ `[NAM: ...]` còn phải điền, kèm số dòng.
4. Mục nào trong checklist của `STYLE.md` chưa đạt, nếu có.

Không tóm tắt lại nội dung bài.

## Git

- Commit message tiếng Việt, ngắn: `Viết nháp: <slug>`, `Sửa theo review: <slug>`, `Tách post FB: <slug>`.
- Không commit file `.env` hay bất kỳ API key nào.
