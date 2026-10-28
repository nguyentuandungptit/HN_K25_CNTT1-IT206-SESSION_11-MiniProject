**BÀI KIỂM TRA** 

# **BỐI CẢNH CHUNG**

Công ty ABC có 300 nhân viên văn phòng. Mỗi sáng, nhân viên phải xuống sảnh ghi tên vào sổ đặt cơm trưa trước 9h30 và chọn 1 trong 4 suất ăn do nhà bếp nấu. Bộ phận hành chính đếm sổ, gọi điện báo số lượng cho nhà bếp, cuối tháng cộng tiền và trừ vào lương.

Những vấn đề đang gặp:

* Nhân viên đi công tác hoặc làm từ xa không đặt được suất ăn.

* Sổ giấy hay bị ghi nhầm tên và nhầm món.

* Hành chính mất khoảng 45 phút mỗi sáng chỉ để tổng hợp số liệu.

* Nhà bếp không biết trước tỷ lệ chọn từng món nên thường xuyên nấu thừa hoặc thiếu.

* Nhân viên không tự tra được trong tháng mình đã đặt bao nhiêu bữa và hết bao nhiêu tiền.

Công ty quyết định xây dựng ứng dụng SmartCanteen để giải quyết các vấn đề trên. Bạn là thành viên của Scrum Team nhận dự án này.

# **BÀI 1 – PHÂN RÃ YÊU CẦU**

**Cho Epic: "Đặt và quản lý suất ăn của nhân viên".**

a) Viết 2 Feature thuộc Epic trên.

| Mã | Feature | Phạm vi |
| :---: | ----- | ----- |
| F-01 | **Đặt và hủy suất ăn trực tuyến** | Nhân viên chọn ngày, chọn 1 trong 4 suất, đặt/hủy trước giờ chốt; áp dụng cả khi đi công tác, làm từ xa |
| F-02 | **Báo cáo và đối soát chi phí ăn trưa** | Tổng hợp số suất theo món cho nhà bếp, tính tiền theo tháng cho nhân viên và hành chính |

b) Viết 2 User Story theo đúng cấu trúc "Là… tôi muốn… để…", mỗi story thuộc một Feature khác nhau ở câu a.

**US-01 (thuộc F-01):**
> Là **nhân viên**, tôi muốn **đặt suất ăn cho ngày mai trên điện thoại trước 9h30**, để **tôi không phải xuống sảnh ghi sổ và vẫn có suất ăn kể cả khi đang đi công tác hoặc làm từ xa**.

**US-02 (thuộc F-02):**
> Là **nhân viên hành chính**, tôi muốn **xem báo cáo tổng hợp số suất theo từng món của ngày mai ngay sau 9h30**, để **tôi gửi số lượng chính xác cho nhà bếp trước 10h mà không phải đếm sổ và gọi điện thủ công**.

c) Nêu 1 hạng mục công việc thuộc Epic này nhưng là Task kỹ thuật chứ không phải User Story, và giải thích ngắn gọn vì sao.

> **Task: Thiết kế và khởi tạo schema cơ sở dữ liệu cho Epic (bảng `employee`, `dish`, `meal_order`, `order_item`) kèm script migration và dữ liệu mẫu cho môi trường dev.**

**Vì sao là Task chứ không phải User Story:** công việc này không tạo ra giá trị quan sát được từ phía người dùng cuối, không có vai trò người dùng nào và không viết được theo mẫu "Là… tôi muốn… để…". Nó là công việc kỹ thuật bắt buộc để US-01 và US-02 có thể chạy được, nên được ước lượng và theo dõi như một task trong Sprint Backlog.

# **BÀI 2 – CHẨN ĐOÁN VÀ VIẾT LẠI USER STORY** 

Hai User Story dưới đây do một thành viên mới viết. Với mỗi story: chỉ ra tiêu chí INVEST bị vi phạm rõ nhất, giải thích trong 1 câu, rồi viết lại cho đạt chuẩn.

**Story A:**

**Tiêu chí INVEST bị vi phạm rõ nhất: Testable (kiểm chứng được).**
"Cảm thấy hài lòng", "chạy nhanh", "dễ dùng" là cảm nhận chủ quan, không có ngưỡng đo nên không thể viết Acceptance Criteria và không thể xác nhận đạt/không đạt khi hết Sprint.

**Viết lại:**

*"Là người dùng, tôi muốn ứng dụng chạy nhanh và dễ dùng để tôi cảm thấy hài lòng."*

> **US-A:** Là **nhân viên**, tôi muốn **hoàn tất việc đặt một suất ăn trong tối đa 3 lần chạm và dưới 30 giây, với các bước không quá 3 màn hình**, để **tôi đặt được cơm ngay cả khi chỉ có 1 phút trước giờ chốt 9h30**.

**AC gợi ý:** Given nhân viên đã đăng nhập và đang ở trang chủ, When chọn "Đặt suất ăn hôm nay" và chọn 1 món, Then hệ thống hiển thị xác nhận đặt thành công trong vòng ≤ 2 giây và tổng số lần chạm không vượt quá 3.

**Story B:**

*"Là nhân viên, tôi muốn có đầy đủ tính năng quản lý bữa trưa gồm đặt suất, hủy suất, đổi món, xem lịch sử, xem công nợ tháng, xuất báo cáo và đánh giá món ăn, để tôi chủ động với bữa trưa của mình."*

**Tiêu chí INVEST bị vi phạm rõ nhất: Small (đủ nhỏ).**
Story gộp 7 tính năng độc lập vào một hạng mục nên không thể ước lượng chính xác, không thể hoàn thành trong một Sprint và không thể nghiệm thu dứt điểm (đồng thời kéo theo vi phạm Independent và Estimable).

**Viết lại (tách nhỏ, giữ lại 1 story nguyên tử):**

> **US-B:** Là **nhân viên**, tôi muốn **đổi món cho suất ăn đã đặt trước 9h30 của ngày ăn**, để **tôi vẫn ăn được món mình thích khi thực đơn thay đổi mà không mất suất**.

Các phần còn lại được tách thành story riêng và đưa về Product Backlog để ưu tiên dần:
- US-B1: đặt suất ăn cho ngày mai
- US-B2: hủy suất trước giờ chốt
- US-B3: xem lịch sử đặt và số tiền phải trả trong tháng
- US-B4: xuất báo cáo tổng hợp (thực chất là story của hành chính, không phải của nhân viên)
- US-B5: đánh giá món ăn sau bữa trưa

# **BÀI 3 – VIẾT ACCEPTANCE CRITERIA** 

Cho User Story sau:

*"Là nhân viên, tôi muốn hủy suất cơm đã đặt trước 9h30 của ngày ăn, để tôi không bị tính tiền bữa mình không ăn."*

Viết 3 Acceptance Criteria theo cấu trúc Given – When – Then vào bảng dưới. Yêu cầu: AC-01 cho luồng thành công, AC-02 cho trường hợp quá giờ hủy, AC-03 do bạn tự chọn (một trường hợp ngoại lệ khác). Mỗi tiêu chí đúng được 1,0 điểm.

| Mã | Nội dung tiêu chí |
| :---: | ----- |
| **AC-01** | **Given** nhân viên đã đặt 1 suất ăn cho ngày ăn 12/11 và hiện tại là 8h00 ngày 11/11 (trước giờ chốt 9h30), **When** nhân viên mở suất ăn đó, bấm "Hủy suất" và xác nhận, **Then** suất ăn chuyển sang trạng thái "Đã hủy", biến mất khỏi báo cáo gửi nhà bếp, và không được cộng vào công nợ tháng của nhân viên. |
| **AC-02** | **Given** nhân viên đã đặt 1 suất ăn cho ngày ăn hôm nay và hiện tại là 9h45 (đã quá giờ chốt 9h30), **When** nhân viên bấm "Hủy suất", **Then** hệ thống không thực hiện hủy, hiển thị thông báo "Đã quá giờ chốt 9h30, không thể hủy suất ăn hôm nay", giữ nguyên trạng thái "Đã đặt" và vẫn tính tiền suất ăn đó vào công nợ tháng. |
| **AC-03** | **Given** suất ăn của nhân viên đã ở trạng thái "Đã hủy" (do hủy thành công trước đó), **When** nhân viên mở lại suất ăn đó và bấm "Hủy suất" lần nữa, **Then** hệ thống không tạo thêm bản ghi hủy, hiển thị thông báo "Suất ăn này đã được hủy trước đó", và số tiền công nợ tháng không thay đổi. |

# **BÀI 4 – ƯU TIÊN VÀ LẬP KẾ HOẠCH SPRINT**

Product Backlog của dự án SmartCanteen đã được ước lượng như sau. Velocity của nhóm trong 3 Sprint gần nhất lần lượt là 18, 22 và 20 Story Point. Sprint kế tiếp kéo dài 2 tuần, nhân sự không thay đổi.

**a) Điền mức ưu tiên MoSCoW cho từng hạng mục, sau đó giải trình lựa chọn cho 2 hạng mục bất kỳ.**

| Mã | Hạng mục | Story Point | MoSCoW |
| :---: | ----- | :---: | :---: |
| SC-01 | Nhân viên đặt suất ăn cho ngày hôm sau | 5 | **Must** |
| SC-02 | Nhân viên hủy suất ăn trước giờ chốt | 3 | **Must** |
| SC-03 | Hành chính xem báo cáo tổng hợp số suất theo món mỗi ngày | 8 | **Should** |
| SC-04 | Nhân viên xem lịch sử đặt và số tiền phải trả trong tháng | 5 | **Should** |
| SC-05 | Nhân viên đánh giá món ăn sau bữa trưa | 3 | **Could** |
| SC-06 | Đăng nhập bằng tài khoản nội bộ của công ty | 8 | **Must** |
| SC-07 | Chia sẻ thực đơn tuần lên fanpage công ty | 2 | **Won't** (Sprint này) |

Giải trình:

- **SC-06 (Must, 8 SP):** đây là điều kiện tiên quyết về kỹ thuật – không có đăng nhập thì không xác định được "suất ăn này của ai", không gắn được công nợ với nhân viên và không phân quyền được giữa nhân viên với hành chính. Mọi story khác đều phụ thuộc vào nó, nên nếu thiếu thì cả Epic không chạy được, dù bản thân nó không phải là tính năng mà nhân viên mong đợi.
- **SC-07 (Won't, 2 SP):** chỉ là kênh truyền thông, không giải quyết bất kỳ vấn đề nào trong 5 vấn đề đang gặp (đặt hộ, ghi nhầm, mất 45 phút tổng hợp, nấu thừa/thiếu, không tra được công nợ). Ngoài ra fanpage có thể đăng thực đơn thủ công, chi phí cơ hội gần bằng 0 → loại khỏi Sprint này, cân nhắc lại ở Sprint sau khi có API thực đơn.

**b)Chọn các hạng mục đưa vào Sprint kế tiếp, ghi rõ tổng Story Point và căn cứ lựa chọn.**

| Mã | Hạng mục | SP |
| :---: | ----- | :---: |
| SC-06 | Đăng nhập bằng tài khoản nội bộ công ty | 8 |
| SC-01 | Nhân viên đặt suất ăn cho ngày hôm sau | 5 |
| SC-02 | Nhân viên hủy suất ăn trước giờ chốt | 3 |
| SC-05 | Nhân viên đánh giá món ăn sau bữa trưa | 3 |
| | **Tổng** | **19** |

**Căn cứ lựa chọn:**

1. **Tổng 19 SP ≤ velocity 20 SP**, chừa 1 SP đệm cho rủi ro (Sprint trước nhóm dao động 18–22, không nên nhận đúng trần).
2. **SC-06 + SC-01 + SC-02 (16 SP) là lát cắt dọc tối thiểu chạy được đầu–cuối**: đăng nhập → đặt → hủy. Ba hạng mục này xử lý trực tiếp 3/5 vấn đề: không đặt được khi đi công tác, ghi nhầm tên/món, và bị tính tiền bữa không ăn.
3. **SC-05 (3 SP) lấy vào vì rẻ và có tác dụng tạo vòng phản hồi sớm**; nó cũng cấp dữ liệu đánh giá món để sau này ghép với báo cáo tỷ lệ chọn món.
4. **SC-03 (8 SP) bị hoãn:** nếu lấy SC-03 thì phải bỏ SC-01 hoặc SC-02 – tức là hy sinh luồng cốt lõi để lấy báo cáo, trong khi hành chính vẫn có thể đọc số liệu thô từ danh sách đặt suất trong 1–2 Sprint đầu.
5. **SC-04 (5 SP) bị hoãn vì phụ thuộc dữ liệu:** story này chỉ có ý nghĩa khi đã tích lũy được dữ liệu đặt/hủy của ít nhất một chu kỳ lương; đưa vào Sprint 2 sẽ kiểm thử được bằng dữ liệu thật.

**c)Viết Sprint Goal cho Sprint đó.**

> **"Trong Sprint này, nhân viên đăng nhập được bằng tài khoản nội bộ công ty và tự đặt – hủy suất ăn cho ngày mai trên điện thoại trước 9h30, đồng thời gửi được đánh giá món sau bữa trưa, để từ ngày đầu vận hành không còn ai phải xuống sảnh ghi sổ giấy và không ai bị tính tiền bữa mình đã hủy đúng hạn."**

**d)Đến hết ngày làm việc thứ 5 của Sprint, số Story Point còn lại được ghi nhận như sau:**

| Ngày làm việc | 0 | 1 | 2 | 3 | 4 | 5 |
| ----- | :---: | :---: | :---: | :---: | :---: | :---: |
| Đường lý tưởng | 20 | 18 | 16 | 14 | 12 | 10 |
| Đường thực tế | 20 | 20 | 19 | 18 | 16 | 15 |

**Nhận xét:**

- Hết ngày 5, thực tế còn **15 SP** so với lý tưởng **10 SP** → **chậm 5 SP**, tương đương khoảng **2,5 ngày công** (1 SP ≈ 0,5 ngày theo nhịp lý tưởng 2 SP/ngày).
- Tốc độ thực tế trong 5 ngày đầu chỉ đạt **1 SP/ngày** (5 SP / 5 ngày), bằng **một nửa** nhịp cần thiết.
- **Ngày 1 không hoàn thành được hạng mục nào** (20 → 20) và ngày 2 chỉ được 1 SP: dấu hiệu điển hình của việc bị chặn ngay từ đầu (rất có thể là SC-06 đăng nhập SSO đang chờ bên IT cấp quyền) hoặc công việc bị chia nhỏ chưa đủ.
- Với 5 ngày còn lại và 15 SP, nhóm cần **3 SP/ngày** – gấp 3 lần tốc độ hiện tại. Nếu giữ nguyên phạm vi, Sprint gần như chắc chắn **không đạt Sprint Goal** và sẽ trượt khoảng 4–5 SP.

**Hành động cụ thể đề xuất:**

> Trong buổi Daily Scrum sáng ngày 6, xác định chính xác hạng mục đang bị chặn (ưu tiên kiểm tra SC-06), **cắt SC-05 (3 SP) ra khỏi Sprint** để bảo vệ Sprint Goal, đồng thời **dồn 2 người đang làm SC-05 sang gỡ chặn SC-06**; nếu chặn không gỡ được trong ngày 6 thì hạ phạm vi SC-06 xuống phương án dùng tài khoản nội bộ tạm thời để không kéo cả Sprint.

Sau khi cắt SC-05, phạm vi còn **16 SP**, khối lượng còn lại **12 SP** trong 5 ngày = **2,4 SP/ngày** – vẫn căng nhưng nằm trong vùng khả thi nếu blocker được gỡ ngay trong ngày 6. Đồng thời cập nhật lại burndown và ghi nhận đây là bài học cho Sprint Retrospective: cần tách story lớn hơn nữa và kiểm tra dependency với IT trước khi cam kết Sprint.
