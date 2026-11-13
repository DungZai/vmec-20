# VMEC-20 · Trợ lý sức khỏe tinh thần

Thiết kế trợ lý tiếng Việt cho sinh viên và người mới đi làm từ 18 tuổi. Người dùng có thể trò chuyện, thử sàng lọc tâm trạng và thực hành bài tập tự chăm sóc có nguồn. Khi xuất hiện tín hiệu nguy cơ, ứng dụng ưu tiên màn hình an toàn và đưa ra lựa chọn liên hệ con người. Bản demo dùng dữ liệu giả lập. AI hỗ trợ ban đầu và không chẩn đoán, kê đơn hay thay thế chuyên gia.

## Hồ sơ thiết kế

| Hạng mục | Tài liệu |
| --- | --- |
| Brief một trang | [Brief VMEC-20](docs/VMEC-20-Brief.docx) |
| Yêu cầu sản phẩm | [PRD](docs/PRD.md) |
| Wireframe và luồng thao tác | [Mở wireframe trên GitHub Pages](https://dungzai.github.io/vmec-20/docs/wireframe.html) · [Tệp HTML](docs/wireframe.html) |
| Nhật ký sử dụng AI | [Hướng dẫn và mẫu AI log](ai-logs/README.md) |

Mở wireframe trực tuyến hoặc clone repo rồi mở `docs/wireframe.html` trong trình duyệt. Chọn **Luồng UI** để xem sơ đồ thao tác. Thử cả hai vai trò và các tình huống an toàn. Các thao tác chuyển ca trong wireframe là mô phỏng.

```powershell
git clone https://github.com/DungZai/vmec-20.git
```

## Làm việc trên GitHub

1. Tạo issue ghi phạm vi và tiêu chí nghiệm thu. Dùng mã kịch bản tổng hợp khi mô tả lỗi an toàn.
2. Tạo nhánh từ `main`. Với thay đổi có dùng AI, tạo một mục trong `ai-logs/` từ mẫu và đính kèm kết quả kiểm tra.
3. Mở pull request, liên kết issue và mục AI log nếu có. Với thay đổi liên quan tới an toàn, nguồn tài nguyên hoặc chia sẻ dữ liệu, mời người phụ trách phần đó duyệt các kịch bản tương ứng trong PRD.

Ai có link đều xem được repo. Chủ repo có thể mời thành viên vào **Settings → Collaborators** để làm việc chung. GitHub tải mẫu PR từ nhánh mặc định. [Hướng dẫn GitHub về mẫu pull request](https://docs.github.com/en/communities/using-templates-to-encourage-useful-issues-and-pull-requests/creating-a-pull-request-template-for-your-repository)
