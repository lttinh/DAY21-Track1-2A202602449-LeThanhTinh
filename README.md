# Lab 21 — Phân tích rủi ro AI qua case study thực tế

- **Họ và tên:** Lê Thanh Tình
- **MSSV / mã học viên:** 2A202602449
- **Lớp:** Track1
- **Ngành đã chọn:** Y tế / trợ lý sức khỏe

> Các mức rủi ro dưới đây là đánh giá định tính phục vụ bài tập, không phải kết luận pháp lý hay tư vấn y khoa. Bài viết chỉ dùng dữ liệu tổng hợp công khai.

## 1. Industry Risk Snapshot

| Nội dung | Đánh giá của tôi và lý do |
| --- | --- |
| Những tác hại chính có thể xảy ra | AI có thể bỏ sót bệnh nặng, chẩn đoán/phân luồng sai, đưa lời khuyên có hại, tạo quá nhiều cảnh báo, phân biệt đối xử hoặc làm lộ dữ liệu sức khỏe. Người bị ảnh hưởng gồm bệnh nhân, người thân, nhân viên y tế và bệnh viện. |
| Mức độ high-stakes | **Cao.** Kết quả AI có thể tác động đến quyết định đi cấp cứu, phát hiện và điều trị kịp thời, hoặc quyền tiếp cận chăm sóc bổ sung. Sai sót có thể dẫn đến tổn thương nghiêm trọng hoặc tử vong. |
| Dữ liệu nhạy cảm có thể được sử dụng | Triệu chứng, chẩn đoán, thuốc, xét nghiệm, hình ảnh y khoa, bệnh sử, dữ liệu di truyền và sức khỏe tâm thần; tuổi, giới, chủng tộc; thông tin định danh, bảo hiểm và chi phí khám chữa bệnh. |
| Nhu cầu human review | **Cao.** Bác sĩ/điều dưỡng phải kiểm tra trước quyết định chẩn đoán, phân luồng, điều trị hoặc phân bổ nguồn lực. Đơn vị triển khai cần theo dõi sai âm, sai dương và hiệu năng theo nhóm dân số; tình huống khẩn cấp hoặc độ tin cậy thấp phải được chuyển ngay cho người thật. |

## 2. Case study 1 — Symptom checker chẩn đoán và phân luồng chưa chính xác

### Brief Case

- **Tổ chức / sản phẩm AI:** 23 symptom checker công khai tại Anh, Mỹ, Hà Lan và Ba Lan; nghiên cứu của Semigran và cộng sự.
- **Thời gian, địa điểm / bối cảnh:** Audit công bố trên *The BMJ* ngày 08/07/2015; dùng 45 tình huống bệnh nhân chuẩn hóa, chia đều thành cấp cứu, không cấp cứu và có thể tự chăm sóc.
- **AI được dùng để làm gì:** Người dùng nhập triệu chứng để nhận danh sách chẩn đoán khả dĩ và/hoặc khuyến nghị mức độ chăm sóc.
- **Vấn đề hoặc sự kiện đáng chú ý:** Các công cụ có thiếu sót ở cả chẩn đoán và phân luồng. Đây là đánh giá bằng tình huống chuẩn hóa, không phải thống kê tổn hại thực tế.
- **Số liệu có nguồn:** Trong **770** lượt đánh giá chẩn đoán, chẩn đoán đúng đứng đầu đạt **34%** (KTC 95%: 31–37%); trong **532** lượt đánh giá phân luồng, khuyến nghị phù hợp đạt **57%** (52–61%). Riêng ca cấp cứu, phân luồng phù hợp đạt **80%** (75–86%).
- **Nguồn:** Hannah L. Semigran và cộng sự, “Evaluation of symptom checkers for self diagnosis and triage: audit study” — *The BMJ* 351:h3480 — 08/07/2015 — [DOI 10.1136/bmj.h3480](https://www.bmj.com/content/351/bmj.h3480), Abstract, Results và Tables 2–4.
- **Phân biệt bằng chứng và nhận định:** **Nguồn xác nhận** các tỷ lệ hiệu năng trên bộ tình huống. **Tôi suy luận** rằng người dùng tin tuyệt đối vào kết quả sai có thể trì hoãn khám hoặc dùng dịch vụ không cần thiết. Nghiên cứu không chứng minh các lỗi này đã trực tiếp gây thương tích ngoài đời và không đại diện cho mọi symptom checker hiện nay.

### Harm Map Worksheet

| Trường | Phân tích của tôi |
| --- | --- |
| High-risk moment | Người có triệu chứng cấp cứu dùng khuyến nghị của symptom checker để quyết định có đi cấp cứu hay không. |
| Stakeholder bị ảnh hưởng | Bệnh nhân; người thân, nhân viên cấp cứu và cơ sở y tế cũng chịu ảnh hưởng từ quyết định trì hoãn hoặc phân luồng quá mức. |
| Failure mode | **Harmful advice / escalation failure / over-reliance:** công cụ khuyến nghị mức chăm sóc không phù hợp; người dùng xem kết quả như chẩn đoán y khoa. |
| Layer bắt đầu lỗi | **Model và Grounding:** thực nghiệm cho thấy hạn chế về chẩn đoán/phân luồng. **UX/Safety** có thể làm tăng rủi ro nếu không cảnh báo hoặc chuyển cấp; bài báo không đủ chi tiết để xác quyết lớp gốc cho mọi công cụ. |
| Harm xảy ra là gì? | **Nguy cơ, chưa được nghiên cứu xác nhận là hậu quả thực tế:** bệnh nhân cấp cứu có thể trì hoãn điều trị; bệnh nhân nhẹ có thể lo lắng và đi khám không cần thiết. |
| Harm lens | **Injury**, **misinformation**; phụ: **opportunity loss** do mất cơ hội điều trị sớm. |
| Severity | **Critical** với ca cấp cứu bị phân luồng thấp; **Medium** với phân luồng quá mức. |
| Scale | **Medium trong nghiên cứu:** 23 công cụ, 45 tình huống, 770 lượt chẩn đoán và 532 lượt phân luồng. Chưa thể ngoại suy thành số bệnh nhân thật. |
| Probability | **Medium (nhận định của tôi):** độ chính xác phân luồng chung 57%, ca cấp cứu 80%. Đây không phải xác suất tổn hại thực tế. |
| Frequency | **Medium–High trong bài kiểm thử:** lỗi lặp lại ở nhiều công cụ và tình huống; chưa đủ dữ liệu về tần suất ngoài đời. |
| Vì sao? | Severity cao vì chậm xử lý cấp cứu có thể gây tổn thương nghiêm trọng. Số liệu nguồn chỉ đo đầu ra đúng/sai trên tình huống chuẩn hóa. Cần cảnh báo rõ, phát hiện dấu hiệu đỏ và chuyển nhân viên y tế. |

## 3. Case study 2 — Epic Sepsis Model bỏ sót sepsis và tạo gánh nặng cảnh báo

### Brief Case

- **Tổ chức / sản phẩm AI:** Epic Systems — Epic Sepsis Model (ESM), mô hình dự đoán sepsis tích hợp trong hồ sơ sức khỏe điện tử.
- **Thời gian, địa điểm / bối cảnh:** Nghiên cứu hồi cứu tại Michigan Medicine, Hoa Kỳ, trên các ca nhập viện từ 06/12/2018 đến 20/10/2019; công bố trên *JAMA Internal Medicine* ngày 21/06/2021.
- **AI được dùng để làm gì:** Tính điểm mỗi 15 phút để cảnh báo bác sĩ về nguy cơ bệnh nhân phát triển sepsis.
- **Vấn đề hoặc sự kiện đáng chú ý:** Kiểm định độc lập cho thấy khả năng phân biệt và hiệu chỉnh kém tại cơ sở nghiên cứu; ở ngưỡng 6, mô hình vừa bỏ sót nhiều ca sepsis vừa tạo nhiều cảnh báo, có nguy cơ gây “mệt mỏi cảnh báo”.
- **Số liệu có nguồn:** **27.697 bệnh nhân**, **38.455 lượt nhập viện**, trong đó **2.552 (7%)** có sepsis. AUC theo lượt nhập viện **0,63** (KTC 95%: 0,62–0,64). Ở ngưỡng 6, độ nhạy **33%**, PPV **12%**; ESM không phát hiện **1.709/2.552 ca sepsis (67%)**, đồng thời đạt ngưỡng cảnh báo ở **6.971/38.455 lượt (18%)**.
- **Nguồn:** Andrew Wong và cộng sự, “External Validation of a Widely Implemented Proprietary Sepsis Prediction Model in Hospitalized Patients” — *JAMA Internal Medicine* — 21/06/2021 — [DOI 10.1001/jamainternmed.2021.2626](https://jamanetwork.com/journals/jamainternalmedicine/fullarticle/2781307), Abstract, Results, Table 2 và Discussion.
- **Phân biệt bằng chứng và nhận định:** **Nguồn xác nhận** hiệu năng và số lượt bị bỏ sót trong kiểm định hồi cứu; các cảnh báo trong phân tích chủ yếu là giả lập. **Tôi suy luận** rằng phụ thuộc quá mức có thể làm chậm nhận diện sepsis và quá nhiều cảnh báo có thể làm giảm chú ý. Nghiên cứu không chứng minh mô hình trực tiếp gây tử vong.

### Harm Map Worksheet

| Trường | Phân tích của tôi |
| --- | --- |
| High-risk moment | Bệnh nhân tiến triển sepsis nhưng ESM chưa vượt ngưỡng, hoặc nhân viên phải xử lý quá nhiều cảnh báo có giá trị dự đoán dương thấp. |
| Stakeholder bị ảnh hưởng | Bệnh nhân nội trú, bác sĩ/điều dưỡng, đội phản ứng sepsis, bệnh viện và người thân. |
| Failure mode | **False negative, false positive và over-reliance:** bỏ sót ca thật; cảnh báo nhiều ca không tiến triển sepsis; con người có thể quá tin hoặc dần bỏ qua cảnh báo. |
| Layer bắt đầu lỗi | **Model/Grounding:** hiệu năng và hiệu chỉnh kém khi kiểm định ngoài. **UX/Safety** liên quan ngưỡng và thiết kế cảnh báo; nguồn không đủ để quy toàn bộ lỗi cho một lớp. |
| Harm xảy ra là gì? | **Nguy cơ:** ca sepsis bị bỏ sót có thể chậm điều trị; cảnh báo dày có thể tăng tải nhận thức và che khuất cảnh báo quan trọng. Nghiên cứu không đo thương tích do ESM gây ra. |
| Harm lens | **Injury**, **opportunity loss** và tác hại vận hành. |
| Severity | **Critical** cho bỏ sót sepsis; **High** cho alert fatigue. |
| Scale | **High trong mẫu:** 38.455 lượt nhập viện; 1.709 ca sepsis không được nhận diện ở ngưỡng đã chọn. Đây chỉ là một trung tâm học thuật. |
| Probability | **High đối với bỏ sót trong mẫu ở ngưỡng 6:** 67% ca sepsis không được nhận diện. Đây không phải xác suất gây hại và có thể đổi theo bệnh viện/ngưỡng. |
| Frequency | **High trong mô phỏng hồi cứu:** 18% lượt nhập viện đạt ngưỡng dù không tính cảnh báo lặp; vận hành thật có thể có quy tắc giảm cảnh báo. |
| Vì sao? | Sepsis cần phát hiện sớm nên hậu quả tiềm tàng nghiêm trọng. Tuy nhiên nghiên cứu đơn trung tâm, hồi cứu; không được đồng nhất “mô hình bỏ sót” với “bác sĩ bỏ sót”. Cần kiểm định địa phương, tối ưu ngưỡng và giữ quyết định ở bác sĩ. |

## 4. Case study 3 — Thiên lệch chủng tộc trong thuật toán quản lý sức khỏe dân số

### Brief Case

- **Tổ chức / sản phẩm AI:** Một thuật toán thương mại dùng rộng rãi tại Hoa Kỳ để chọn bệnh nhân vào chương trình quản lý chăm sóc nguy cơ cao; bài nghiên cứu không nêu tên sản phẩm trong nội dung chính.
- **Thời gian, địa điểm / bối cảnh:** Dữ liệu bệnh nhân chăm sóc ban đầu trong hợp đồng theo rủi ro tại một bệnh viện học thuật lớn ở Hoa Kỳ giai đoạn 2013–2015; đăng trên *Science* ngày 25/10/2019.
- **AI được dùng để làm gì:** Xếp điểm rủi ro để xác định bệnh nhân có nhu cầu sức khỏe phức tạp và phân bổ hỗ trợ bổ sung.
- **Vấn đề hoặc sự kiện đáng chú ý:** Thuật toán dùng **chi phí y tế** làm biến đại diện cho **nhu cầu sức khỏe**. Do chi tiêu không phản ánh bình đẳng mức độ bệnh, ở cùng điểm rủi ro, bệnh nhân Da đen có tình trạng bệnh nặng hơn bệnh nhân Da trắng.
- **Số liệu có nguồn:** Nếu sửa thiên lệch bằng cách dự đoán nhu cầu sức khỏe thay vì chi phí, tỷ lệ bệnh nhân Da đen trong nhóm nhận hỗ trợ bổ sung sẽ tăng từ **17,7% lên 46,5%**.
- **Nguồn:** Ziad Obermeyer, Brian Powers, Christine Vogeli và Sendhil Mullainathan, “Dissecting racial bias in an algorithm used to manage the health of populations” — *Science* 366(6464), 447–453 — 25/10/2019 — [DOI 10.1126/science.aax2342](https://escholarship.org/uc/item/6h92v832), Abstract và nội dung bài báo.
- **Phân biệt bằng chứng và nhận định:** **Nguồn xác nhận** chênh lệch, cơ chế proxy chi phí và kết quả mô phỏng sửa mục tiêu. **Tôi suy luận** rằng người không được chọn có thể mất cơ hội nhận quản lý chăm sóc hữu ích. Nghiên cứu không định lượng thương tích hay tử vong cá nhân do thuật toán.

### Harm Map Worksheet

| Trường | Phân tích của tôi |
| --- | --- |
| High-risk moment | Điểm thuật toán quyết định bệnh nhân nào vượt ngưỡng và được mời vào chương trình chăm sóc bổ sung. |
| Stakeholder bị ảnh hưởng | Bệnh nhân Da đen có nhu cầu cao, bệnh nhân khác cạnh tranh nguồn lực, bác sĩ, đơn vị quản lý và hệ thống y tế. |
| Failure mode | **Bias/fairness:** biến mục tiêu “chi phí” là proxy không phù hợp cho “mức độ bệnh/nhu cầu chăm sóc”, gây phân bổ bất bình đẳng. |
| Layer bắt đầu lỗi | **Grounding/Model:** bài toán và nhãn dự đoán không bám đúng mục tiêu lâm sàng. Mô hình có thể dự đoán chi phí chính xác nhưng vẫn sai với mục đích phân bổ theo nhu cầu. |
| Harm xảy ra là gì? | **Đã được nguồn xác nhận:** bệnh nhân Da đen bị đại diện thấp trong nhóm nhận hỗ trợ dù nhu cầu tương đương hoặc cao hơn. **Nguy cơ suy luận:** chậm tiếp cận chăm sóc có thể làm bệnh nặng hơn. |
| Harm lens | **Opportunity loss**, **dignity loss** và bất công phân bổ. |
| Severity | **High:** quyết định tác động quyền tiếp cận nguồn lực y tế; chưa đủ bằng chứng để xếp Critical. |
| Scale | **High:** nguồn mô tả thuật toán dùng rộng và ảnh hưởng hàng triệu bệnh nhân; 17,7% → 46,5% cho thấy chênh lệch lớn trong nhóm được chọn. |
| Probability | **High trong bối cảnh nghiên cứu:** thiên lệch xuất hiện có hệ thống ở cùng mức điểm rủi ro. Không ngoại suy sang mọi thuật toán y tế. |
| Frequency | **High khi thuật toán dùng lặp lại:** mỗi chu kỳ chọn bệnh nhân có thể tái tạo chênh lệch nếu mục tiêu chi phí không được sửa. Đây là nhận định dựa trên cơ chế nghiên cứu. |
| Vì sao? | Chênh lệch tiếp cận y tế khiến chi phí lịch sử không phải thước đo trung lập của bệnh tật. Cần dùng chỉ dấu sức khỏe trực tiếp, audit theo nhóm, kiểm tra ngưỡng và cho bác sĩ quyền bổ sung người bị bỏ sót. |

## 5. Kết luận và biện pháp giảm thiểu chung

Ba case cho thấy hiệu năng trung bình hoặc độ chính xác kỹ thuật không đủ bảo đảm AI y tế có trách nhiệm. Rủi ro có thể bắt đầu từ năng lực mô hình, dữ liệu/biến đại diện, cách đặt ngưỡng, giao diện cảnh báo hoặc thiếu quy trình chuyển cho người thật.

Các biện pháp ưu tiên: kiểm định độc lập và tại nơi triển khai; báo cáo sai âm/sai dương theo nhóm dân số; thiết kế cơ chế chuyển cấp cứu; hiển thị giới hạn và độ không chắc chắn; giữ bác sĩ trong vòng quyết định; giám sát drift và sự cố; tối thiểu hóa dữ liệu; có quy trình khiếu nại, sửa sai và tạm dừng hệ thống.

## 6. Tài liệu tham khảo

1. Semigran, H. L., et al. (2015). [Evaluation of symptom checkers for self diagnosis and triage: audit study](https://www.bmj.com/content/351/bmj.h3480). *The BMJ*, 351, h3480. https://doi.org/10.1136/bmj.h3480
2. Wong, A., et al. (2021). [External Validation of a Widely Implemented Proprietary Sepsis Prediction Model in Hospitalized Patients](https://jamanetwork.com/journals/jamainternalmedicine/fullarticle/2781307). *JAMA Internal Medicine*, 181(8), 1065–1070. https://doi.org/10.1001/jamainternmed.2021.2626
3. Obermeyer, Z., et al. (2019). [Dissecting racial bias in an algorithm used to manage the health of populations](https://escholarship.org/uc/item/6h92v832). *Science*, 366(6464), 447–453. https://doi.org/10.1126/science.aax2342
