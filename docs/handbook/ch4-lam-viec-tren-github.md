# Chương 4 — Làm việc trên GitHub

> **Trạng thái:** Bản thảo v0 · 21/9/2026 · Ban thư ký rà soát trước khi merge vào `main`.

## 4.1. Tổ chức

Hiệp hội dùng GitHub Organization `vba-org` làm nơi soạn thảo cộng tác và công bố tài liệu kỹ thuật, tài liệu nội bộ công khai và mã nguồn.

| Hạng mục | Hiện trạng |
|---|---|
| Organization | `github.com/vba-org` |
| Gói dịch vụ | GitHub Team, cấp qua chương trình GitHub for Nonprofits |
| Owner | Chủ tịch; `[CẦN XÁC NHẬN: danh sách owner đầy đủ — khuyến nghị tối thiểu 2, tối đa 4]` |
| Xác thực | Đăng nhập qua Google Workspace `blockchain.vn` |
| 2FA | **Bắt buộc** với toàn bộ thành viên org |

## 4.2. Quy ước đặt tên kho

| Dạng | Mẫu | Ví dụ |
|---|---|---|
| Tài liệu | `<chủ-đề>` hoặc `<chủ-đề>-docs` | `vba-handbook` |
| Báo cáo, nghiên cứu | `report-<chủ-đề>-<năm>` | `report-digital-asset-2026` |
| Góp ý chính sách | `policy-<tên-văn-bản>` | `policy-nd-huong-dan-luat-71` |
| Mã nguồn | `<tên-dự-án>` | `vba-did-toolkit` |
| Mẫu, biểu mẫu | `templates-<lĩnh-vực>` | `templates-van-ban` |

Tên kho viết thường, dùng dấu gạch ngang, không dấu tiếng Việt.

## 4.3. Mức hiển thị

| Mức | Dùng cho | Điều kiện |
|---|---|---|
| **Public** | Tài liệu nội bộ công khai, báo cáo đã công bố, mã nguồn mở | Đã qua bước 5–6 của Chương 3, hoặc README ghi rõ "đang xây dựng" |
| **Internal** | Dự thảo đang soạn, tài liệu chỉ dành cho hội viên | Mặc định cho kho mới |
| **Private** | Hồ sơ nhân sự, tài chính, tài liệu có ràng buộc bảo mật | Owner phê duyệt từng trường hợp |

Kho mới tạo ở mức `Internal`. Chuyển sang `Public` là một hành động có kiểm soát: cần xác nhận của Ban thư ký rằng nội dung đã qua thẩm định Chương 3.

## 4.4. Phân quyền

| Vai trò GitHub | Cấp cho | Được làm |
|---|---|---|
| Owner | Chủ tịch và người được chỉ định | Quản trị org, thanh toán, bảo mật |
| Admin (repo) | Chủ trì kho | Cấu hình kho, quản lý cộng tác viên |
| Maintain | Thư ký tiểu ban phụ trách | Quản lý issue, PR, release; không đổi cấu hình bảo mật |
| Write | Thành viên tiểu ban, cộng tác viên thường xuyên | Tạo branch, mở PR |
| Triage | Cộng tác viên mới | Phân loại issue, không sửa mã |
| Read | Hội viên | Đọc, bình luận |

Cấp quyền **qua team, không cấp trực tiếp cho cá nhân**. Gợi ý team: `@vba-org/ban-thu-ky`, `@vba-org/tieu-ban-<tên>`, `@vba-org/cong-tac-vien`.

Rà soát quyền truy cập 6 tháng/lần. Thành viên rời tiểu ban hoặc chấm dứt cộng tác được gỡ khỏi team trong 5 ngày làm việc.

## 4.5. Branch

| Branch | Mục đích |
|---|---|
| `main` | Bản hiện hành. **Được bảo vệ** |
| `docs/handbook-chN` | Soạn chương N của sổ tay |
| `docs/<chủ-đề>` | Soạn tài liệu khác |
| `feat/<mô-tả-ngắn>` | Tính năng mới (kho mã nguồn) |
| `fix/<mô-tả-ngắn>` | Sửa lỗi |

**Bảo vệ `main`:** cấm push trực tiếp; yêu cầu pull request; tối thiểu 1 approval; yêu cầu giải quyết hết conversation; cấm force-push và xóa branch.

## 4.6. Commit và pull request

**Commit** theo dạng `<loại>: <mô tả ngắn, tiếng Việt có dấu>`. Các loại: `docs`, `feat`, `fix`, `chore`, `refactor`.

```
docs: bổ sung bảng thẩm quyền ký vào chương 3
fix: sửa số hiệu Nghị định 126/2024/NĐ-CP ở chương 1
```

**Pull request** phải nêu: thay đổi gì, vì sao, đã kiểm tra viện dẫn pháp lý chưa, còn mục `[CẦN XÁC NHẬN]` nào. PR sửa nội dung có tính bản chất của tài liệu đã công bố phải dẫn chiếu quyết định phê duyệt tương ứng (Chương 3).

**CODEOWNERS.** Mỗi thư mục tài liệu có chủ sở hữu nội dung; GitHub tự động yêu cầu họ review.

```
/docs/handbook/ch1-*.md   @vba-org/ban-thu-ky
/docs/handbook/ch4-*.md   @vba-org/ban-thu-ky
```

Không tự merge PR của chính mình, trừ khi kho chỉ có một người duy trì và thay đổi thuần túy là lỗi chính tả.

## 4.7. Issue

Dùng issue cho: đề xuất nội dung mới, báo lỗi dữ kiện, câu hỏi về quy trình. Nhãn tối thiểu: `noi-dung`, `phap-ly`, `can-xac-nhan`, `quy-trinh`, `khan`.

Issue gắn nhãn `phap-ly` phải được đầu mối pháp chế trả lời trước khi PR liên quan được merge.

## 4.8. Bảo mật và giới hạn

- **Không commit** khóa API, token, mật khẩu, dữ liệu cá nhân hội viên, tài liệu có ràng buộc bảo mật. Bật secret scanning và push protection cho toàn bộ kho.
- Nếu lỡ commit bí mật: **thu hồi/đổi khóa trước**, xóa khỏi lịch sử sau. Coi như đã lộ.
- GitHub **không phải** hệ thống lưu trữ hồ sơ pháp lý. Bản gốc có chữ ký, dấu lưu theo mục 3.6.
- Nội dung trong kho `Public` là phát ngôn công khai của Hiệp hội trên thực tế, kể cả khi ghi "dự thảo". Áp dụng Chương 5 ngay từ commit đầu tiên.
- Tài khoản cá nhân dùng cho công việc Hiệp hội phải bật 2FA và liên kết email công vụ.

## 4.9. Quy trình soạn một chương sổ tay

1. Mở issue nêu phạm vi chương và người chủ trì.
2. Tạo branch `docs/handbook-chN` từ `main`.
3. Soạn, commit nhỏ và thường xuyên; đánh dấu mọi dữ kiện chưa kiểm chứng bằng `[CẦN XÁC NHẬN]`.
4. Mở PR ở trạng thái draft khi đạt ~50% để lấy ý kiến sớm.
5. Chuyển sang ready for review; gắn CODEOWNER và đầu mối pháp chế nếu có viện dẫn.
6. Merge bằng squash; xóa branch; đóng issue; cập nhật cột Trạng thái ở README.
