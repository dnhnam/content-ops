---
title: "Claude Code cloud session: giao Claude giữ kho nội dung mà không cần biết code"
slug: cloud-session-cho-content-ops
keyword: claude code cloud session
meta_description: "Dựng repo chỉ có file Markdown để Claude Code cloud session viết bài đúng giọng, rồi review như review code. Không cần biết code."
brief: briefs/cloud-session-cho-content-ops.md
status: draft
word_count: 1215
published_url: ""
---

Bạn mở khung chat để nhờ Claude viết một bài mới. Việc đầu tiên vẫn là dán lại đoạn hướng dẫn giọng văn, dán brief, rồi dán thêm một bài cũ làm mẫu. Sang bài tiếp theo, bạn dán lại đúng ba thứ đó một lần nữa. Nếu những thứ này nằm sẵn trong một thư mục để Claude tự đọc mỗi lần làm việc thì sao? Bài này kể cách tôi dựng kho nội dung bằng claude code cloud session, trong đó toàn bộ chỉ là file chữ.

## Key Takeaways

- Cloud session không chỉ dành cho lập trình viên, vì repo của bạn có thể chỉ chứa file Markdown.
- File `CLAUDE.md` và `STYLE.md` thay cho việc dán đi dán lại prompt vào khung chat.
- Bạn review bài nháp bằng cách xem diff và comment từng dòng, giống cách lập trình viên review code.
- Cloud session có giới hạn về mạng và connector, nên một số bước vẫn phải làm ở máy của bạn.

## Cloud session không chỉ dành cho code

Tôi nhận được một coupon dùng cloud session của Claude. Mở ra, tôi gặp ngay dòng yêu cầu phải có một GitHub repository (kho lưu file kèm lịch sử mọi lần sửa) thì mới bắt đầu được. Câu hỏi đầu tiên của tôi là: cái này dùng để làm gì, khi tôi không viết code?

Câu trả lời hóa ra đơn giản hơn tôi nghĩ. Cloud session là Claude chạy trên một máy chủ, mở sẵn repo của bạn, đọc file trong đó rồi làm việc. Repo không bắt buộc chứa code. Nó chứa file Markdown (file chữ thuần, định dạng bằng vài ký hiệu đơn giản) cũng chạy được, và với người làm nội dung thì thế là vừa đủ.

Hãy nhìn từ phía người làm marketing. Mỗi bài blog cần ít nhất ba thứ: brief, quy tắc giọng văn, bài cũ để tham chiếu. Ba thứ này vốn đã là chữ. Chúng chỉ đang nằm sai chỗ, tức là nằm trong đầu bạn, trong Google Docs, trong lịch sử chat, và bạn là người vận chuyển giữa các nơi đó. Repo đưa cả ba về một chỗ, Claude mở ra là thấy.

Repo chỉ cần chứa chữ, không cần chứa code.

## Một repo content-ops gồm những gì

Ngày 18/10/2026, tôi kết nối GitHub xong và dựng repo `content-ops`. Bên trong có sáu mục:

- `CLAUDE.md`: hướng dẫn cố định, Claude đọc ở đầu mỗi session.
- `STYLE.md`: quy tắc giọng văn.
- `briefs/`: đầu vào của tôi, gồm chủ đề, từ khóa, trải nghiệm thật.
- `drafts/`: bài blog nháp do Claude viết.
- `social/`: post Facebook tách ra từ bài blog.

Mục thứ sáu là `published/`, nơi chứa bài đã đăng. Tôi đặt luật là Claude không được đụng vào đó, trừ khi tôi yêu cầu rõ. Với `briefs/` cũng vậy: Claude chỉ đọc, không sửa. Lý do rất thực tế. Brief là phần trải nghiệm thật của tôi, và nếu AI được phép sửa phần đó thì sớm muộn nó sẽ "làm đẹp" một con số.

Phần tôi tốn công nhất là `STYLE.md`. Tôi không viết mới. Tôi rút gọn từ style guide giọng văn đã làm hồi tháng 9/2026, nên Claude không phải đoán giọng mỗi lần. Tôi để thêm cả một checklist ở cuối file, và `CLAUDE.md` yêu cầu Claude chạy checklist đó trước khi báo xong. Nghĩa là việc "kiểm tra xem bài đã đúng giọng chưa" đã được giao đi, thay vì nằm trên vai tôi.

Còn kết quả thực tế thì sao? [NAM: kết quả bài nháp đầu tiên Claude viết từ repo này: mất bao lâu, phải sửa mấy chỗ, chỗ nào AI làm hỏng việc và bạn sửa thế nào]

Về thời gian chuẩn bị, [NAM: so sánh với cách cũ (dán prompt vào chat): mỗi bài tốn bao nhiêu phút chuẩn bị trước đây và bây giờ]. Tôi nói thẳng là phần so sánh này chỉ có giá trị khi có số thật, nên tôi không ước chừng.

Sáu mục này thay cho cả một đống prompt.

## Review bài như review code

Trong thế giới lập trình, người ta không sửa thẳng vào code của đồng nghiệp. Họ xem diff (phần khác biệt giữa bản cũ và bản mới), comment vào từng dòng, rồi người viết sửa theo. Cách này dùng cho bài blog được luôn.

Quy trình của tôi có năm bước. Tôi tạo brief trong `briefs/`. Claude đọc `STYLE.md` và brief, rồi viết bài vào `drafts/`. Tôi xem diff và comment từng dòng. Claude sửa theo comment. Khi bài ổn, tôi mới nhờ Claude tách thành ba post Facebook. Chuyển bài sang `published/` là bước cuối, và chỉ xảy ra khi tôi bảo.

Điểm hay nhất nằm ở comment từng dòng. Khi chat, bạn thường nói chung chung kiểu "viết lại cho tự nhiên hơn", và Claude phải đoán chỗ nào chưa tự nhiên. Khi comment ngay trên dòng đó, bạn chỉ đúng câu, đúng chữ. Tôi cho rằng đây là khác biệt lớn nhất so với cách chat thông thường, và nó nằm ở chỗ bạn chỉ chỗ sai chính xác đến đâu.

Có hai thái cực mà tôi thấy nhiều người rơi vào. Một bên là tự sửa tay toàn bộ bài AI viết, nên mất luôn lợi thế về thời gian. Bên kia là đăng nguyên bản AI viết, và giọng văn trôi đi lúc nào không hay. Đường giữa tôi chọn là AI viết bản đầu, còn tôi duyệt từng dòng và giữ quyền quyết định cuối cùng.

[NAM: thêm ví dụ thật về một lần review diff trên bài này: bạn comment câu nào, Claude sửa ra sao]

Claude viết, bạn duyệt từng dòng.

## Những giới hạn bạn nên biết trước

Cloud session không làm được mọi thứ, và tôi thà nói ra từ đầu. Mạng trong cloud session bị chặn theo mặc định. Các connector như Canva hay Google Drive cũng chưa dùng được trong cloud session. Hệ quả là hai bước trong quy trình của tôi, đăng bài và tạo ảnh, vẫn phải chạy ở máy cá nhân.

Nghe thì có vẻ phiền, nhưng thật ra nó vạch ra một ranh giới khá rõ. Phần cần chữ và cần suy nghĩ về giọng văn thì giao cho cloud session. Phần cần mạng, cần đăng nhập vào dịch vụ khác thì tôi tự làm. Tôi chấp nhận cách chia này, vì phần việc nặng nhất của tôi là viết và sửa bài, và phần đó chạy được.

Một lưu ý khác: những gì tôi kể ở đây là tình trạng tính đến ngày 18/10/2026. Các giới hạn này có thể thay đổi, nên trước khi dựng repo, bạn hãy tự kiểm tra lại xem cloud session của bạn đang cho phép gì.

Phần nào cần mạng thì làm ở máy.

## Việc làm ngay hôm nay

Cloud session cho content không phức tạp như tên gọi của nó. Thứ làm nên khác biệt là những file chữ bạn viết một lần để Claude đọc mãi mãi. Hôm nay, hãy mở một file mới, đặt tên `STYLE.md`, và chép vào đó mười dòng quy tắc giọng văn mà bạn hay phải nhắc Claude nhiều nhất. Đó là nền của kho nội dung, và bạn dựng được nó trong một buổi chiều.

[NAM: internal link: bài liên quan trên dnhnam.com, ví dụ bài SHUHARI 2026]
