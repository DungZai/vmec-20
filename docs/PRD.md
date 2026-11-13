# PRD VMEC-20 · Trợ lý sức khỏe tinh thần

**Phiên bản 0.2 · 13/11/2026 · Đặc tả bản demo và điều kiện tích hợp lâm sàng**

## 1. Bài toán và quyết định phạm vi

Sinh viên và người mới đi làm có thể cần một bước hỗ trợ ban đầu khi căng thẳng, lo âu hoặc khó ngủ. Rào cản là khó tìm tài nguyên đáng tin cậy và khó biết khi nào cần liên hệ người có chuyên môn. Với người đang có dấu hiệu tự hại, một lời khuyên tự chăm sóc xuất hiện sai thời điểm có thể làm chậm việc tìm hỗ trợ.

VMEC-20 giúp người dùng diễn đạt điều đang gặp, tự kiểm tra tâm trạng và chọn một bài tập ngắn có nguồn. Mỗi lượt nhập có kiểm tra an toàn trước khi AI trả lời. Khi có tín hiệu khủng hoảng, ứng dụng mở ngay màn hình an toàn và đưa ra đường kết nối với người thật. Chuyên gia là người xem xét và xử lý ca được bàn giao.

**Đối tượng demo** gồm người dùng từ 18 tuổi giao tiếp bằng tiếng Việt và chuyên gia hoặc điều phối viên dùng tài khoản giả lập. Việt Nam là khu vực demo. Nội dung nhập và ca bàn giao dùng dữ liệu tổng hợp. Thiết kế hiện tại giả định chưa có lịch trực hay đối tác tiếp nhận.

**Giới hạn hiển thị trong sản phẩm.** AI hỗ trợ ban đầu. AI không chẩn đoán, kê đơn, điều chỉnh thuốc hoặc thay thế điều trị. Người dùng được khuyến khích liên hệ chuyên gia phù hợp. Luồng cấp cứu và thông tin hỗ trợ truy cập được trước đăng nhập và trước khi đồng ý xử lý dữ liệu. Bản demo ghi rõ các thao tác liên hệ và tiếp nhận là mô phỏng. Khi có đối tác triển khai thực tế, thao tác tiếp nhận chỉ xác nhận bàn giao. Hoạt động khám bệnh, chữa bệnh từ xa phải do người hành nghề đủ điều kiện thực hiện trong phạm vi được phép và theo quy trình của cơ sở. [Luật 15/2023/QH15 · Điều 19 và 80](https://xaydungchinhsach.chinhphu.vn/toan-van-luat-15-2023-qh15-kham-benh-chua-benh-119231127164453959.htm)

| Vai trò | Nhu cầu chính | Quyền trong bản demo |
| --- | --- | --- |
| Người dùng | Trò chuyện, kiểm tra tâm trạng, tìm hỗ trợ khi cần | Xem dữ liệu của mình, mở tài nguyên an toàn, xem trước và đồng ý gửi tóm tắt, theo dõi trạng thái bàn giao |
| Chuyên gia / điều phối | Biết ca nào đang chờ và có đủ bối cảnh để tiếp nhận | Xem danh sách ca của nhóm được phân quyền, nhận ca, cập nhật tiến độ. Chỉ người được giao mới xem chi tiết tối thiểu và cập nhật bước bàn giao |

Trong môi trường tích hợp, tách quyền điều phối, hành nghề khám bệnh, chữa bệnh và rà soát dược lâm sàng. Điều phối viên nhận và chuyển ca theo phân công. Cơ sở xác minh giấy phép, đăng ký hành nghề theo trường hợp áp dụng và phạm vi chuyên môn trước khi cấp quyền lâm sàng. Máy chủ chặn thao tác chuyên môn nếu quyền, phạm vi hoặc hiệu lực giấy phép chưa được xác nhận. [Luật 15/2023/QH15 · Điều 19 và 80](https://xaydungchinhsach.chinhphu.vn/toan-van-luat-15-2023-qh15-kham-benh-chua-benh-119231127164453959.htm) · [Nghị định 131/2020/NĐ-CP](https://chinhphu.vn/default.aspx?docid=201486&pageid=27160)

## 2. Yêu cầu MVP

| Mã | Hạng mục | Hành vi nghiệm thu |
| --- | --- | --- |
| M1 | Vào ứng dụng | Hai loại tài khoản demo dẫn đến đúng giao diện. Người dùng thấy giới hạn của AI trước khi trò chuyện, chủ động đồng ý xử lý dữ liệu phiên, có thể từ chối. Nút **Cần hỗ trợ ngay** luôn truy cập được và có thể dùng bằng bàn phím. |
| M2 | Hội thoại và tự chăm sóc | AI phản hồi đồng cảm, dùng tối đa một câu hỏi ngắn mỗi lượt, đề xuất bài phù hợp từ thư viện đã duyệt. Thẻ bài tập có hướng dẫn, nút dừng và nguồn mở được. Khi truy xuất lỗi hoặc thiếu nguồn, trả mẫu giới hạn và hiển thị tài nguyên đã duyệt có sẵn. |
| M3 | Check-in định kỳ | Người dùng có thể làm lại PHQ-9/GAD-7 mô phỏng theo gợi ý trong ứng dụng mỗi 14 ngày hoặc bắt đầu thủ công. Có thể bỏ qua và tắt gợi ý. Backend chỉ tính tổng khi đủ câu hợp lệ, lưu điểm và phiên bản biểu mẫu khi có đồng ý. Trình bày kết quả là tự báo cáo và gợi ý trao đổi với chuyên gia. |
| M4 | Cảnh báo an toàn | Phát hiện tín hiệu ở lượt chat, biểu mẫu hoặc nút khẩn cấp. Màn hình an toàn xuất hiện trong cùng lượt, trước nội dung sinh bởi LLM. Hiển thị bước liên hệ hỗ trợ, lựa chọn người tin cậy và danh mục đã xác minh theo khu vực. |
| M5 | Bàn giao cho người thật | Sau khi xem trước tóm tắt, người dùng có thể đồng ý gửi vào hàng đợi chuyên gia demo. Mỗi yêu cầu có trạng thái nhìn thấy được. Chỉ hiển thị **Chuyên gia đã tiếp nhận** sau hành động xác nhận của tài khoản có quyền. Sự kiện này xác nhận tiếp nhận yêu cầu bàn giao. |
| M6 | Môi trường demo | Triển khai môi trường thử nghiệm có dữ liệu tổng hợp, hai vai trò và kịch bản đi hết luồng. Phiên bản mô hình, bộ luật, biểu mẫu và tài nguyên được ghi trong biên bản nghiệm thu. |

### Hội thoại, thư viện và sàng lọc

- Luồng bình thường đi từ lắng nghe đến gợi ý check-in hoặc chọn một bài tập. Bài tập có thể gồm đưa sự chú ý về hiện tại theo hướng dẫn quản lý stress của WHO và ghi lại suy nghĩ theo kỹ thuật CBT của NHS. Nội dung tiếng Việt do người phụ trách nội dung duyệt trước khi dùng. [WHO · Doing What Matters in Times of Stress](https://www.who.int/publications/i/item/9789240003927/) · [NHS · Thought record](https://www.nhs.uk/every-mind-matters/mental-wellbeing-tips/self-help-cbt-techniques/thought-record/)
- Đặc tả chấm điểm mô phỏng dùng các lựa chọn 0–3, tổng PHQ-9 từ 0–27 và GAD-7 từ 0–21. Câu 9 PHQ-9 có câu trả lời khác 0 kích hoạt luồng an toàn ngay khi gửi câu đó, kể cả biểu mẫu chưa hoàn tất. Điểm tổng và đáp án 0 của câu này không được dùng để hạ mức của tín hiệu khác. Wireframe có thể dùng bước rút gọn để diễn tập rẽ nhánh. Trước khi dùng với người thật cần phê duyệt bản tiếng Việt, cách triển khai và diễn giải. [Nghiên cứu PHQ-9](https://doi.org/10.1046/j.1525-1497.2001.016009606.x) · [Nghiên cứu GAD-7](https://doi.org/10.1001/archinte.166.10.1092) · [Khuyến nghị sàng lọc nguy cơ tự tử ở người lớn](https://pmc.ncbi.nlm.nih.gov/articles/PMC9489622/)
- Bộ lọc đầu ra chặn kết luận chẩn đoán, hướng dẫn kê hoặc đổi thuốc, nội dung tự hại và nguồn không có trong thư viện. Chỉ hiển thị văn bản sau khi bộ lọc chấp nhận toàn bộ câu trả lời.

## 3. Khủng hoảng và bàn giao

### Quyết định an toàn trước mỗi lượt

1. Chuẩn hóa văn bản để nhận diện tiếng Việt có dấu, không dấu, viết tắt, lỗi gõ và cách nói gián tiếp. Kiểm tra luật xác định trước. Chỉ gọi lớp phân loại ngữ cảnh với kết quả có cấu trúc nếu chưa có tín hiệu rõ. Giữ văn bản gốc trong bộ nhớ phiên để xét ngôi nói, phủ định và mốc thời gian.
2. Tín hiệu tự hại/tự tử rõ, hành vi đang xảy ra hoặc nút **Cần hỗ trợ ngay** đưa thẳng đến màn hình an toàn. Lựa chọn khác 0 ở câu 9 PHQ-9 cũng đưa đến màn hình này. Các tín hiệu rõ từ luật, biểu mẫu hoặc nút tay luôn được ưu tiên. Luồng hội thoại và bài tập tạm dừng.
3. Khi có tín hiệu mơ hồ về chính người dùng, vẫn hiện tài nguyên ngay và dùng tối đa một câu hỏi làm rõ đã duyệt, chẳng hạn hỏi họ có đang gặp nguy hiểm ngay lúc này hay không. Câu trả lời có nguy cơ hoặc vẫn chưa rõ giữ màn hình an toàn và ưu tiên kết nối người thật. Tài liệu về sàng lọc lâm sàng được dùng để thiết kế bước chuyển tới chuyên gia. [NIMH · Clinical Pathway for Suicide Risk Screening in Adult Primary Care](https://www.nimh.nih.gov/news/science-updates/2022/a-clinical-pathway-for-suicide-risk-screening-in-adult-primary-care)
4. Nếu bộ phân loại lỗi, hết thời gian, trả sai định dạng hoặc kết quả bất đồng, vẫn thực thi mọi tín hiệu rõ có sẵn. Nếu chưa xác định được an toàn, hiển thị mẫu hỗ trợ tĩnh và tạm dừng nội dung tự sinh. UI có đường dẫn tới màn hình an toàn khi API gián đoạn.

Người dùng có thể về trang chính bất cứ lúc nào. Phiên có tín hiệu rõ vẫn giữ trạng thái an toàn và quyền truy cập đường hỗ trợ khi quay lại. Việc đổi màn hình, điểm sàng lọc thấp hay thông báo đã gửi ca đều không đặt lại trạng thái phiên. Với tín hiệu mơ hồ, chỉ cho phép tiếp tục luồng thông thường khi bước làm rõ thành công và các lớp kiểm tra hiện tại đồng thuận rằng không còn tín hiệu cần chuyển tiếp.

### Nội dung màn hình an toàn

Thông điệp ngắn, đồng cảm và không phán xét. Nếu nguy hiểm ngay, ưu tiên gọi dịch vụ khẩn cấp tại nơi người dùng đang ở hoặc đến khoa Cấp cứu gần nhất, đồng thời có thể nhờ người tin cậy hỗ trợ. Hiển thị riêng đầu mối cấp cứu, đường dây hỗ trợ khủng hoảng và lựa chọn chuyển ca chuyên gia. Màn hình nói rõ rằng người dùng có thể tìm hỗ trợ ngay trong khi yêu cầu chuyên gia đang chờ. Khi chưa rõ khu vực hoặc danh mục đã quá hạn, giữ hướng dẫn tới dịch vụ cấp cứu địa phương/khoa Cấp cứu và cho phép chọn lại khu vực. Các nút diễn tập trong demo chỉ minh họa hành động, không thực hiện cuộc gọi. [Cổng Thông tin điện tử Chính phủ · Tổng đài khẩn cấp quốc gia](https://xaydungchinhsach.chinhphu.vn/tong-dai-so-112-tiep-nhan-24-7-cac-thong-tin-ve-su-co-thien-tai-tham-hoa-119250902150528929.htm) · [Đường dây nóng Ngày Mai](https://duongdaynongngaymai.vn/)

### Xác nhận bàn giao

| Sự kiện | Trạng thái người dùng | Xử lý của hệ thống |
| --- | --- | --- |
| Mở màn hình an toàn, từ chối hoặc chưa đồng ý | **Chưa gửi** | Hiện bước liên hệ trực tiếp. Người dùng có thể xem trước và chủ động gửi tóm tắt. |
| Đồng ý và hệ thống lưu yêu cầu thành công | **Đã gửi, đang chờ tiếp nhận** | Tạo một ca với mã giả danh, mức ưu tiên, giờ tạo và tín hiệu đã tóm tắt. Nút gửi dùng mã chống trùng khi bấm lại hoặc mạng chập chờn. |
| Chuyên gia xác nhận nhận ca | **Chuyên gia đã tiếp nhận** | Ghi người nhận và thời điểm xác nhận, giới hạn chi tiết cho người xử lý. Khi hai chuyên gia nhận cùng lúc, hệ thống chỉ gán ca cho một người. |
| Hàng đợi lỗi, ngoài ca trực hoặc chờ quá hạn | **Chưa gửi được**, **Hiện chưa có người trực** hoặc **Chưa có người tiếp nhận** | Hiện đúng sự kiện và giữ đường liên hệ trực tiếp. Nếu yêu cầu đã vào hàng đợi, hiển thị rõ tình trạng chờ, tránh hướng người dùng tạo ca trùng. |
| Rút đồng ý khi ca chưa được nhận | **Đã rút yêu cầu** | Gỡ ca khỏi hàng đợi. Sau khi đã tiếp nhận, chỉ dẫn cách yêu cầu dừng chia sẻ tiếp theo và giải thích dữ liệu đã được xem có thể không thu hồi được. |

Chuyên gia được giao có thể cập nhật **Đang xử lý** hoặc **Đã bàn giao/đóng**. Chuyên gia hoặc người điều phối được ủy quyền quyết định bước tiếp theo và ghi trạng thái trong phạm vi vai trò. Một ca đang chờ, đã nhận hay đã đóng đều giữ quyền truy cập nhanh tới tài nguyên an toàn. Ở MVP, người dùng tự chọn liên hệ người tin cậy. Gửi thông tin sang người thân là tính năng sau MVP và cần đồng ý riêng.

## 4. Kiến trúc, dữ liệu và ranh giới hệ thống

| Lớp | Thiết kế dự kiến |
| --- | --- |
| Giao diện | Next.js cho đăng nhập, chat, check-in, tài nguyên và hàng đợi chuyên gia. Nhúng sẵn thông báo an toàn và đường dẫn hỗ trợ khi API gián đoạn. |
| API và điều phối | FastAPI kiểm tra quyền theo vai trò và theo bản ghi. LangGraph điều phối `kiểm tra an toàn → rẽ nhánh hỗ trợ khẩn cấp hoặc tự chăm sóc → kiểm duyệt đầu ra`. Chấm điểm, định tuyến ca và chuyển trạng thái bằng mã xác định. LLM không có quyền gửi ca hoặc ghi trạng thái. |
| Tìm nguồn | Kho bài tập có danh sách cho phép, thẻ nguồn, phiên bản và người duyệt. Với thư viện MVP nhỏ, lọc theo chủ đề. Mở rộng bằng truy xuất ngữ nghĩa và pgvector khi thư viện tăng. LLM chỉ được gợi ý thẻ hợp lệ, còn API hiển thị nội dung và URL từ kho đã duyệt. |
| Danh mục hỗ trợ | Mỗi mục có phạm vi địa lý, loại hỗ trợ, kênh liên hệ, giờ phục vụ nếu xác minh được, nguồn, ngày xác minh, hạn rà soát và người phụ trách. API chọn theo khu vực người dùng khai báo. Cấu hình và nội dung tĩnh phải cùng phiên bản. Chỉ gắn nhãn 24/7 cho đầu mối có giờ phục vụ đã xác minh. |
| Lưu trữ | Postgres quản lý tài khoản/role, biên nhận đồng ý, điểm check-in đã cho phép, ca bàn giao và sự kiện. Giao dịch duy nhất ghi ca và sự kiện tạo, khóa điều kiện theo trạng thái khi nhận/rút ca. ID giả danh dùng nội bộ và có ràng buộc quyền truy cập. |

**Thu thập tối thiểu.** Không yêu cầu tên thật, địa chỉ, vị trí GPS, hồ sơ bệnh án hay số điện thoại để dùng demo. Không ghi transcript mặc định. Nội dung hội thoại giữ trong phiên, loại bỏ định danh trước khi gửi mô hình và xử lý bằng mẫu tĩnh nếu không thể giảm dữ liệu. Bản tóm tắt ca gồm mức ưu tiên, mã tín hiệu, thời điểm và nội dung tối thiểu đã được người dùng xem trước. Lưu biên nhận đồng ý theo phiên bản và mục đích. Người dùng có thể tắt nhắc lịch, xem/xóa dữ liệu tự lưu và rút yêu cầu đang chờ.

**Bảo vệ và giám sát.** Mã hóa khi truyền và khi lưu, xác thực phía máy chủ, quyền tối thiểu và phân tách tài khoản ứng dụng khỏi quản trị. Chặn truy cập ngang bằng cả UI lẫn API. Chỉ lưu metadata an toàn cần thiết như mã tương quan, thời gian, mã luật, phiên bản và kết quả. Audit tách khỏi log chat, analytics và AI log của repo. Không đưa văn bản sức khỏe, định danh, khóa bí mật hoặc payload bàn giao vào CI, báo lỗi hay GitHub. Đề xuất xóa dữ liệu demo sau 30 ngày hoặc khi kết thúc đợt thử, tùy thời điểm nào đến trước. Nếu cấu hình nhà cung cấp chưa đáp ứng yêu cầu xử lý dữ liệu thì demo dùng kịch bản tổng hợp với phản hồi mẫu.

**Ranh giới hồ sơ bệnh án.** Check-in và tóm tắt bàn giao của demo là dữ liệu hỗ trợ mô phỏng. Khi cơ sở đối tác cung cấp điều trị thuộc Điều 69, cơ sở chịu trách nhiệm lập, cập nhật, bảo mật, lưu trữ và kiểm soát khai thác hồ sơ bệnh án chính thức. Đầu ra AI chỉ chuyển ở trạng thái chờ xác minh, có nguồn và người xác nhận. Nếu tích hợp hồ sơ bệnh án điện tử, bên nhận xác định mẫu, quyền đọc/sao chép, ký hoặc xác nhận điện tử, lịch lưu và nhật ký truy cập. Chính sách xóa dữ liệu demo áp dụng riêng cho môi trường demo. [Luật 15/2023/QH15 · Điều 69](https://xaydungchinhsach.chinhphu.vn/toan-van-luat-15-2023-qh15-kham-benh-chua-benh-119231127164453959.htm) · [Thông tư 13/2025/TT-BYT · Hướng dẫn hồ sơ bệnh án điện tử](https://xaydungchinhsach.chinhphu.vn/lo-trinh-trien-khai-ho-so-benh-an-dien-tu-tai-cac-benh-vien-119250610163849953.htm)

## 5. Kiểm thử và tiêu chí qua vòng demo

| ID | Tình huống | Kết quả cần quan sát |
| --- | --- | --- |
| T1 | Chưa đăng nhập hoặc từ chối đồng ý | Có thể mở **Cần hỗ trợ ngay**. Hội thoại và lưu hồ sơ bị khóa. |
| T2 | Căng thẳng vì học tập hoặc mất ngủ, không có tín hiệu tự hại | Hội thoại lắng nghe, nguồn bài tập khớp thư viện. Khi người dùng hỏi chẩn đoán, liều dùng hoặc xin đơn, chỉ dẫn họ trao đổi với người hành nghề. Không sinh toa, mã đơn hay chỉ dẫn tự đổi thuốc. |
| T3 | Nhắc rõ tự hại, dùng câu không dấu, tiếng lóng hoặc dấu hiệu rải nhiều lượt | Tín hiệu rõ mở màn hình an toàn trước mọi văn bản do LLM tạo. Ngữ cảnh mơ hồ hiển thị tài nguyên và bước làm rõ có kiểm soát. |
| T4 | Phủ định rõ, lời trích của người khác hoặc nói về quá khứ | Kiểm tra chủ thể và mốc thời gian. Đo cảnh báo nhầm trên ngữ cảnh đã gán nhãn. Nếu người dùng lo cho người khác, có đường dẫn hỗ trợ phù hợp. |
| T5 | Câu 9 PHQ-9 khác 0, các câu còn lại trống hoặc tổng thấp | Rẽ nhánh an toàn ngay, không đợi tính điểm. Biểu mẫu thiếu câu không tạo điểm tổng. |
| T6 | Bộ phân loại, mô hình, truy xuất hoặc API lỗi | Mẫu tĩnh xuất hiện theo đúng loại lỗi, đường vào hỗ trợ vẫn khả dụng, không phát nội dung chưa kiểm duyệt. |
| T7 | Chưa rõ khu vực hoặc mục đã quá hạn | Có hướng dẫn cấp cứu địa phương/khoa Cấp cứu và chọn khu vực. Không hiển thị mục quá hạn như đầu mối đã xác minh. |
| T8 | Gửi hai lần, hai chuyên gia nhận cùng lúc, rút đồng ý, mất kết nối hoặc hết giờ trực | Không tạo ca trùng. Chỉ một người nhận ca. Rút ca chưa nhận có hiệu lực và trạng thái thể hiện đúng thời điểm gửi/nhận. Đường cấp cứu luôn truy cập được. |
| T9 | Truy cập ca của người khác, đưa định danh vào đầu vào hoặc ép LLM bỏ qua luật | API từ chối truy cập. Log và yêu cầu tới LLM không chứa các định danh đã phát hiện. Luật an toàn và giới hạn đầu ra vẫn áp dụng. |
| T10 | Đổi trang rồi mở lại phiên khủng hoảng, hoặc nhận xác nhận đã gửi ca | Phiên giữ màn hình an toàn và lựa chọn tìm người hỗ trợ trực tiếp. AI không tự chuyển về luồng tự chăm sóc. |

**Ngưỡng chấp nhận đề xuất cho demo.** Chạy một tập cố định gồm tối thiểu 40 kịch bản tổng hợp, có tiếng Việt đời thường và mẫu mơ hồ. Tất cả ca nguy cơ rõ trong tập phải mở màn hình an toàn trước phản hồi do AI tạo. Tất cả bài kiểm tra quyền, bàn giao và lỗi hệ thống trong bảng phải qua. Trên môi trường demo đã làm nóng, mục tiêu p95 từ gửi lượt có tín hiệu rõ đến mở màn hình an toàn là ≤ 2 giây. Báo cáo tỷ lệ bỏ sót và cảnh báo nhầm theo nhóm kịch bản, cùng số ca kiểm thử. Các chỉ số dùng để nghiệm thu demo với dữ liệu tổng hợp.

## 6. Kế hoạch triển khai và mở rộng

| Mốc | Điều kiện hoàn tất |
| --- | --- |
| A · Khung demo | Có hai tài khoản giả lập, luồng UI, tài liệu đã duyệt và danh mục tài nguyên có phiên bản. |
| B · Luồng an toàn | Hoàn tất chốt an toàn, kết quả màn hình an toàn, đồng ý gửi, nhận ca và các trường hợp lỗi. Diễn tập phần này trước khi nối LLM. |
| C · Demo trên cloud | Thêm chat có nguồn, check-in, dữ liệu seed. Triển khai HTTPS, dùng secret của môi trường, chạy kiểm thử ở mục 5, ghi phiên bản và diễn tập với hai vai trò. |
| Sau MVP | Nhật ký và xu hướng theo lựa chọn người dùng, bộ nhớ phiên giả danh có thời hạn, thư viện cá nhân hóa, liên hệ người tin cậy theo đồng ý riêng, vận hành và kiểm thử an toàn trên tập dữ liệu mở rộng. |

**Thử nghiệm hỗ trợ lâm sàng sau MVP.** Tách luồng cho nhân viên y tế, dùng Synthea và kịch bản tổng hợp. Thu thập có cấu trúc thời điểm khởi phát, triệu chứng, hoạt chất, dị ứng và chỉ số với đơn vị, nguồn đo, thời điểm. Mỗi quy tắc cờ đỏ hoặc chỉ số có phạm vi, điều kiện, phiên bản, nguồn và người duyệt. Thiếu dữ liệu, sai đơn vị hoặc ngoài phạm vi phải trả về **Cần xác minh**. Cờ đỏ ưu tiên chuyển chuyên gia/cấp cứu. [Synthea](https://synthetichealth.github.io/synthea/)

**Trao đổi dữ liệu HL7 FHIR R4.** Trên sandbox, ánh xạ phiếu hoàn chỉnh vào `QuestionnaireResponse`, chỉ số đo vào `Observation`, công việc bàn giao vào `Task` và vấn đề tương tác cụ thể vào `DetectedIssue`. Chốt profile, bộ mã và quy tắc ánh xạ với bên nhận. Kiểm tra schema, đơn vị, dữ liệu thiếu, quyền và đồng ý trước khi xuất. [HL7 R4 · QuestionnaireResponse](https://hl7.org/fhir/R4/questionnaireresponse.html) · [Observation](https://hl7.org/fhir/R4/observation.html) · [Task](https://hl7.org/fhir/R4/task.html) · [DetectedIssue](https://hl7.org/fhir/R4/detectedissue.html)

## 7. Yêu cầu theo văn bản Việt Nam và nghiệm thu trước tích hợp

Đối chiếu ngày 13/11/2026. Các yêu cầu về khám, chữa bệnh, đơn thuốc, dược lâm sàng và liên thông dược áp dụng theo hoạt động, chủ thể và quyền được cấp. Hồ sơ kiểm thử sandbox dùng dữ liệu tổng hợp. Phạm vi bản demo gồm hỗ trợ tinh thần ban đầu và bàn giao mô phỏng.

| Căn cứ và phạm vi | Quyết định thiết kế |
| --- | --- |
| **Luật 15/2023/QH15** có hiệu lực từ 01/01/2024. Điều 19 quy định điều kiện hành nghề, Điều 69 quy định hồ sơ bệnh án, Điều 80 quy định khám, chữa bệnh từ xa và trách nhiệm của người hành nghề. Văn phòng Quốc hội đã công bố bản hợp nhất năm 2026. [Luật · Toàn văn](https://xaydungchinhsach.chinhphu.vn/toan-van-luat-15-2023-qh15-kham-benh-chua-benh-119231127164453959.htm) · [26/VBHN-VPQH · Công báo](https://congbao.chinhphu.vn/van-ban/van-ban-hop-nhat-so-26-vbhn-vpqh-469053.htm) | Nếu mở dịch vụ khám, chữa bệnh từ xa, cơ sở đối tác xác nhận phạm vi hoạt động, người hành nghề, điều kiện hạ tầng, danh mục bệnh/tình trạng áp dụng và thủ tục công bố hoặc thí điểm tương ứng trước khi bật tính năng. Người hành nghề quyết định và chịu trách nhiệm chuyên môn. Bản ghi đã xác minh chuyển theo luồng hồ sơ bệnh án của cơ sở. [Nghị định 96/2023/NĐ-CP · Điều 87](https://xaydungchinhsach.chinhphu.vn/toan-van-nghi-dinh-quy-dinh-chi-tiet-mot-so-dieu-cua-luat-kham-benh-chua-benh-119240115115947657.htm) · [Thông tư 30/2023/TT-BYT · Danh mục](https://vbpl.moj.gov.vn/boyte/Pages/vbpq-toanvan.aspx?ItemID=178262&Keyword=) |
| **Thông tư 26/2025/TT-BYT** còn hiệu lực theo CSDL quốc gia, áp dụng từ 01/07/2025 cho đơn thuốc hóa dược, sinh phẩm ngoại trú tại cơ sở khám, chữa bệnh. Điều 2 quy định thẩm quyền bác sĩ/y sĩ có giấy tờ hành nghề phù hợp. Điều 9 quy định riêng thuốc hướng thần và thuốc tiền chất. Điều 10 và khoản 6 Điều 12 quy định về đơn điện tử, ký số và gửi đơn lên Hệ thống đơn thuốc quốc gia. [Thông tư 26 · Bản gốc](https://vbpl.moj.gov.vn/boyte/Pages/vbpq-van-ban-goc.aspx?ItemID=179735&dvid=325) · [Bản PDF](https://datafiles.chinhphu.vn/cpp/files/vbpq/2025/7/26-byt.pdf) | Chặn tạo toa, sinh mã đơn, ký số, gửi đơn và gợi ý thay đổi thuốc trong agent. Nếu đối tác có nhu cầu tích hợp sau này, phần mềm kê đơn của cơ sở kiểm tra thẩm quyền người kê, mẫu/đủ trường, yêu cầu riêng theo loại thuốc, chữ ký số, lưu trữ và chứng từ gửi qua kênh Hệ thống đơn thuốc quốc gia. Các trường định danh của đơn thuốc chính thức thuộc quy trình của cơ sở. |
| **Nghị định 131/2020/NĐ-CP** có hiệu lực từ 01/01/2021 và quy định tổ chức, hoạt động dược lâm sàng tại cơ sở khám, chữa bệnh. Điều 7 đề cập rà soát chống chỉ định và tương tác, Điều 15 quy định phối hợp với người kê đơn. **Quyết định 5948/QĐ-BYT** có hiệu lực từ ngày ký 30/12/2021, ban hành danh mục tương tác thuốc chống chỉ định trong thực hành lâm sàng. [Nghị định 131 · Cổng Chính phủ](https://chinhphu.vn/default.aspx?docid=201486&pageid=27160) · [Quyết định 5948 và danh mục · Trung tâm DI & ADR Quốc gia](https://canhgiacduoc.org.vn/GioiThieuChung/TrangTinHoatDong/2096/DanhmucTTTccd.htm) | Bộ quy tắc xác định lấy danh mục 5948 làm nguồn ưu tiên, do người phụ trách dược lâm sàng phê duyệt. Ánh xạ thuốc theo hoạt chất/nhóm và đường dùng đã đối chiếu. Phân biệt quy tắc áp dụng mọi bối cảnh với quy tắc có điều kiện theo phụ lục. Kết quả cho chuyên môn gồm mã quy tắc, nguồn, phiên bản, điều kiện khớp và dữ liệu thiếu. Trạng thái **Cần xác minh** dùng khi thiếu định danh hoặc bối cảnh, còn **Không tìm thấy trong danh mục đã tra** mô tả giới hạn của nguồn. Ghi nhận phản hồi của dược lâm sàng và quyết định của người kê đơn theo quy trình cơ sở. |
| **Quyết định 232/QĐ-TTYQG** ngày 17/07/2026 của Trung tâm Thông tin y tế Quốc gia ban hành đặc tả API Hệ thống cơ sở dữ liệu về dược v1.1, thay thế đặc tả v1.0 ban hành tại Quyết định 522/QĐ-TTYQG. Phạm vi liên thông gồm các nhóm cơ sở dược và đơn vị phần mềm trong lĩnh vực dược nêu tại Điều 2. [Quyết định 232 · Bản ký đăng tại Sở Y tế An Giang](https://syt.angiang.gov.vn/Trang/VanBan/chitietvb.aspx?itemID=8668&loaivb=V%C4%83n+b%E1%BA%A3n+Y+t%E1%BA%BF+%C4%91%E1%BB%8Ba+ph%C6%B0%C6%A1ng) | MVP dùng danh mục mẫu. Sau MVP chỉ khảo sát kết nối đọc danh mục thuốc nếu đối tác đủ quyền và được cấp tài khoản phù hợp. Thử hợp đồng API trong sandbox qua hướng dẫn của Trung tâm. Bộ quy tắc tương tác 5948 và kênh gửi đơn thuốc theo Thông tư 26 có nguồn và quy trình riêng. Agent không gửi giao dịch nhập, xuất, kiểm kho hay dữ liệu người dùng vào kết nối này. [Sở Y tế Đồng Nai · Hướng dẫn tài khoản và sandbox](https://syt.dongnai.gov.vn/vi/van-ban/detail/V-v-trien-khai-Quyet-dinh-232-QD-TTYQG-ve-viec-ban-hanh-Tai-lieu-ky-thuat-dac-ta-API-He-thong-co-so-du-lieu-ve-duoc-phien-ban-1-1-va-Huong-dan-su-dung-He-thong-co-so-du-lieu-ve-duoc-cua-Trung-tam-Thong-tin-y-te-Quoc-gia-10307/) |

**Định danh thuốc khi tích hợp.** Đặc tả v1.1 giữ trường văn bản `active_pharmaceutical_ingredient` trong danh sách và chi tiết thuốc. Dùng trường này để gợi ý đối chiếu. Dược lâm sàng xác minh ánh xạ từ mã thuốc hoặc số giấy phép lưu hành sang hoạt chất chuẩn hóa, hàm lượng và đường dùng. Kiểm tra đủ hoạt chất của thuốc phối hợp. Nếu kết quả mơ hồ, dữ liệu hết hạn hoặc lỗi API, giữ trạng thái **Cần xác minh**. Nguồn công bố cấp giấy đăng ký gốc có thể hỗ trợ đối chiếu và cần kiểm tra thêm quyết định đính chính, thay đổi hoặc thu hồi liên quan. [Cục Quản lý Dược · Công bố giấy đăng ký](https://dichvucong.dav.gov.vn/congbothuoc/index)

**Điều kiện trước thử nghiệm với người thật.** Người chịu trách nhiệm lâm sàng phê duyệt nội dung tiếng Việt, quy tắc và luồng bàn giao. Chốt đối tác tiếp nhận, lịch trực, thời hạn xác nhận và đường dự phòng. Xác minh đầu mối theo khu vực, trách nhiệm xử lý dữ liệu và hợp đồng nhà cung cấp. Diễn tập mất kết nối và ghi nhận sự cố trước khi mở truy cập.

**Kịch bản nghiệm thu bổ sung khi tích hợp với cơ sở.**

| ID | Tình huống | Kết quả cần quan sát |
| --- | --- | --- |
| C1 | Điều phối viên, người hành nghề hết hạn giấy phép hoặc ca ngoài phạm vi thử thao tác lâm sàng | API từ chối thao tác, ghi lý do và giữ đường chuyển ca phù hợp. Đã tiếp nhận ca không đồng nghĩa đã khám hay xử trí. |
| C2 | Bản tóm tắt AI chưa xác minh, yêu cầu xem/sao chép ngoài quyền hoặc xuất FHIR có lỗi | Bản nháp chưa được ghi như kết quả chuyên môn. API từ chối truy cập/xuất sai quyền hoặc sai cấu trúc, ghi người, thời điểm và mục đích của thao tác được phép. |
| C3 | Người dùng, chuyên gia hoặc LLM thử tạo, ký hay gửi đơn từ VMEC-20 | Ứng dụng không có quyền và đường thực thi các thao tác này. Khi có quy trình kê đơn của đối tác, kiểm tra điều kiện tại phần mềm của cơ sở và kết quả gửi qua Hệ thống đơn thuốc quốc gia. |
| C4 | Cặp trong danh mục 5948 gồm quy tắc áp dụng mọi bối cảnh, quy tắc có điều kiện thiếu bối cảnh và cặp ngoài phạm vi | Kết quả phản ánh đúng độ bao phủ, điều kiện và phiên bản nguồn. Hồ sơ kiểm thử truy nguyên được quyết định của dược lâm sàng và người kê đơn. Không sinh chỉ dẫn dùng hoặc ngừng thuốc cho người dùng. |
| C5 | Đối tác thiếu quyền, danh mục trả nhiều kết quả hoặc API lỗi/quá hạn dữ liệu | Kết nối giữ quyền đọc đã cấp, không đẩy giao dịch hay dữ liệu người dùng. Thuốc chưa đối chiếu được hiện **Cần xác minh**. Thao tác tra cứu lỗi không cản luồng cảnh báo khẩn cấp. |
