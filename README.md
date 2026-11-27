# 🌾 Rice Field AI

Trang web chat đa năng một file duy nhất (`index.html`) — **chat với agent Rice Field (agent duy nhất, miễn phí)**, **tạo ảnh 8K**, **bói toán huyền học**, **ẩm thực Việt**, và **đọc văn bản thành tiếng** với đầy đủ tùy chỉnh.

Không cần cài đặt, không cần build, không cần server. Mở `index.html` bằng trình duyệt là chạy (khuyến nghị Chrome / Edge / Cốc Cốc bản mới).

---

## 1. Cách chạy

**Cách nhanh nhất:** nhấp đôi vào `index.html`.

**Nếu bạn muốn chạy như một website thật** (ví dụ để dùng trên điện thoại trong cùng wifi):

```bash
cd rice-field-ai
python3 -m http.server 8080
# mở http://localhost:8080
```

> ⚠️ **Quan trọng — chọn cách mở đúng:**
> - **Mở trực tiếp file `index.html` (file://)**: mọi thứ hoạt động, kể cả agent miễn phí + tạo ảnh miễn phí.
> - **Chạy qua http/https (python http.server, hosting, preview)**: nhà cung cấp miễn phí *Pollinations* sẽ chặn bằng Turnstile (lỗi 403) → chat và tạo ảnh sẽ không chạy. App phát hiện và hiển thị hướng dẫn; cách khắc phục duy nhất là **mở trực tiếp file `index.html`**.
> - Bản xem trước trong ứng dụng bị chặn mạng nên phần gọi AI/tạo ảnh sẽ báo lỗi — hãy tải file về máy.

---

## 2. Các khu vực chức năng

| Tab | Nội dung |
|---|---|
| 💬 **Chat AI** | Agent **Rice Field** (duy nhất), chat streaming, sửa tin nhắn & AI trả lời lại ngay tại chỗ, đọc câu trả lời thành tiếng |
| 🎨 **Tạo ảnh AI** | Tạo ảnh từ mô tả + 1–6 ảnh mẫu tham chiếu, xuất **8K (7680×4320)**, xóa từng ảnh, xóa toàn bộ lịch sử |
| 🔮 **Bói toán** | Tarot (78 lá) · Bài Tây (52) · Lenormand (36) · Oracle (36) · Kinh Dịch (64 quẻ) · Tử Vi · Tướng Số — 11 chủ đề, 25+ kiểu trải bài |
| 🍜 **Ẩm thực** | 32 món (mặc định món Việt), 5 miền/loại, tùy chỉnh **số người ăn** tự quy đổi nguyên liệu, nút ảnh tham khảo Google, danh sách đi chợ |
| ⚙️ **Cài đặt** | Thông tin agent, system prompt, temperature, **giọng đọc mặc định**, sáng/tối, xuất–nhập–xóa dữ liệu |

---

## 3. Agent model AI

Rice Field AI hiện có **đúng một agent duy nhất**:

| Agent | Chi tiết |
|---|---|
| 🌾 **Rice Field** | Miễn phí · **không giới hạn lượt chat** · **không cần API key** · không cần đăng ký · không lọc nội dung. Endpoint tương thích OpenAI (`text.pollinations.ai`), model mặc định `openai` (có thể sửa ô *Tên model*). |

- Bấm dấu **?** cạnh ô chọn agent để đọc thông tin agent.
- **Không còn** bất kỳ agent/model nào khác: GPT, Gemini, Claude, Groq, OpenRouter, DeepSeek, Dola, Ollama… đã được **loại bỏ hoàn toàn** khỏi giao diện, cùng toàn bộ phần nhập API key.
- Không có khoá nào được lưu hay gửi đi: app chỉ gửi `Content-Type: application/json` tới endpoint công khai.

## 4. Đọc văn bản thành tiếng (TTS)

Thanh đọc được **ghim cố định ở cuối trang**, dùng chung cho Chat, Bói toán và Ẩm thực:

- ▶ / ⏸ Tạm dừng & phát tiếp
- ⏮ ⏭ Lùi / tới 1 câu, ⏪ ⏩ tua 5%, nút « 10% / 10% »
- **Thanh tiến độ kéo được** — thả ra là đọc đúng đoạn đó
- Tốc độ 0.5×–2×, âm lượng, cao độ
- **Ngôn ngữ: 39 thứ tiếng** (Anh, Nhật, Trung, Hàn, Thái, Pháp, Đức, Ả Rập…)
- **22 kiểu giọng**: nữ, nam, nữ trẻ, nam trẻ, trẻ em gái/trai, người già nam/nữ, robot nam/nữ, kể chuyện, MC thời sự, đọc tin, lồng tiếng nam/nữ miền Nam – miền Bắc, quảng cáo, kinh dị, hùng biện, vui vẻ.
- **Hai bộ máy đọc**: giọng hệ thống/Google (Web Speech) và **Google Dịch — giọng tiếng Việt** (tự chuyển sang giọng hệ thống nếu lỗi mạng).
- Nút 📋 *Dán văn bản để đọc* — đọc bất kỳ nội dung nào.
- Lưu giọng mặc định ở tab **Cài đặt** → mục *Giọng đọc mặc định* (bộ máy đọc, ngôn ngữ, giọng/nhân vật, kiểu giọng, tốc độ, cao độ, âm lượng).

> Giọng thực tế phụ thuộc thiết bị: Windows có Microsoft An/Linh/Nam Minh, Android/iOS có giọng Google, macOS có giọng Việt của Apple. Nếu máy chưa có giọng tiếng Việt, app tự nhắc và chuyển sang Google Dịch.

---

## 5. Tạo ảnh AI

- **Nguồn ảnh duy nhất: Rice Field Image** (Pollinations, `flux`/`turbo`) — **miễn phí, không cần key**. Nhà cung cấp giới hạn **1 ảnh / 45 giây**; app tự phát hiện ảnh thông báo lỗi và **không lưu** vào lịch sử.
- **Ảnh mẫu tham chiếu:** tải lên 1–6 ảnh (mỗi ảnh có nút xóa riêng); mô tả của ảnh mẫu được gửi kèm trong prompt để AI bám đúng nhân vật / bố cục / phong cách.
- **8K:** mọi ảnh được nâng cấp nhiều bước lên **7680×4320** (hoặc 4320×7680 với 9:16) kèm làm nét nhẹ, tải về là file JPEG 8K.
- Mỗi ảnh có **⬇ Tải · 🔍 Xem · 🗑 Xóa**, kèm nút **Xóa toàn bộ lịch sử**.
- Lịch sử lưu bằng **IndexedDB** nên không bị giới hạn dung lượng như localStorage.

---

## 6. Bói toán

Chọn loại → chủ đề → kiểu trải bài → **Rút bài & luận giải**. Kết quả gồm luận giải từng vị trí, tổng kết xu hướng và lời khuyên; có nút **🔊 Đọc kết quả** và **🤖 Nhờ AI luận sâu hơn** (dùng agent đang chọn ở tab Chat).

- **11 chủ đề:** tổng quan, tình duyên, tiền bạc, công việc, tài chính – đầu tư, quá khứ–hiện tại–tương lai, sức khoẻ, gia đình, học tập, định hướng, tâm linh.
- **Kiểu trải bài:** 1 lá, 3 lá, 4 lá, 5 lá, 7 lá, 9 lá (Lenormand 3×3), 10 lá Celtic Cross rút gọn, 2–3 quẻ Kinh Dịch, cùng các dạng riêng cho Tử Vi & Tướng Số.
- Nội dung mang tính tham khảo – giải trí, không thay thế tư vấn y khoa/pháp lý/tài chính.

### 6.1. Lưu · Xem lại · Chụp · Tải âm thanh trải bài

| Nút | Chức năng |
|---|---|
| 💾 **Lưu trải bài** | Lưu **tất cả** trải bài trong phiên (mọi lần bấm Rút bài) vào lịch sử trên máy. Có bộ đếm “chưa lưu”. |
| 📜 **Lịch sử trải bài** | Xem lại toàn bộ bản ghi: ảnh thu nhỏ, thời gian, chủ đề, câu hỏi, các lá. Mỗi bản ghi có: 👁 Xem lại · 🔊 Đọc · ⬇ Tải âm thanh · ⬇ Tải ảnh chụp · 🗑 Xóa. |
| 📸 **Chụp trải bài** | Chụp lại màn hình khu vực trải bài đang hiển thị, **lưu ảnh vào đúng bản ghi** trong lịch sử, đồng thời mở hộp thoại để bạn **chọn vị trí lưu ảnh về máy**. Nếu CDN bị chặn, app tự vẽ **ảnh thiết kế** (khổ 1080px, nền neon) — có nút 🎨 để đổi qua lại. |
| ⬇️ **Tải âm thanh** | Xuất phần đọc thành tệp: **Google Dịch → MP3** hoặc **Thu âm khi đọc → WAV** (miễn phí, không cần key). |
| 🗑 **Xóa lịch sử trải bài** | Xóa hàng loạt toàn bộ bản ghi + ảnh chụp (có xác nhận). |

Ảnh chụp và bản ghi được lưu bằng IndexedDB/localStorage nên vẫn còn sau khi tải lại trang.

### 6.2. Về việc tải âm thanh

- **Google Dịch (miễn phí):** app tải từng câu MP3 rồi ghép thành một tệp duy nhất. Việc này phụ thuộc máy chủ trung gian CORS nên đôi khi bị giới hạn tần suất — khi đó app gợi ý chuyển sang “Thu âm khi đọc”.
- **Thu âm khi đọc (miễn phí, không cần key):** trình đọc đọc to, app thu lại và xuất **WAV**. Cần Chrome/Edge trên máy tính; khi hộp thoại hiện ra chọn **Tab này** + bật **Chia sẻ âm thanh tab**. Đây là cách chắc chắn nhất khi máy chủ trung gian CORS của Google Dịch bị chặn.
- Sau khi tạo xong, trình duyệt sẽ hỏi **vị trí lưu** (File System Access API); nếu không hỗ trợ, tệp vào thư mục “Tải xuống”.

---

## 7. Ẩm thực

- 32 món, mặc định **đặc sản Việt Nam** (phở, bún chả, bún bò Huế, mì Quảng, cơm tấm, bánh xèo, gỏi cuốn, chả giò, cá kho tộ, chè…), có thêm vài món quốc tế.
- Lọc theo vùng miền / loại món / thời gian / độ khó, tìm theo nguyên liệu, sắp xếp, **♡ Yêu thích**, **🎲 Món ngẫu nhiên**.
- **Tùy chỉnh số người ăn 1–50:** nguyên liệu tự quy đổi (kể cả phân số như `1/2 muỗng`), thời gian nấu gợi ý điều chỉnh theo nồi lớn hơn.
- Mỗi món có **📷 Ảnh tham khảo** → mở tìm kiếm hình ảnh Google đúng món đó.
- **🔊 Đọc công thức**, **📋 Copy nguyên liệu**, **🛒 Thêm vào danh sách đi chợ** (gộp nhiều món, copy hoặc đọc thành tiếng).

---

## 8. Giao diện & dữ liệu

- **Sáng / Tối** chuyển ngay bằng nút ☀️/🌙 — màu chữ tự đảo (nền tối → chữ sáng, nền sáng → chữ tối) trên toàn bộ trang.
- Phong cách **neon xanh dương pastel + hồng pastel + trắng**, viền phát sáng mềm, bo tròn.
- Phím tắt: `Enter` gửi, `Shift+Enter` xuống dòng, `Ctrl/Cmd + K` focus ô chat.
- Dữ liệu (chat, ảnh, lịch sử trải bài, cài đặt) lưu cục bộ trên trình duyệt: **Xuất / Nhập / Xóa toàn bộ** trong tab Cài đặt.

---

## 9. Ghi chú kỹ thuật

- Toàn bộ app trong **một file `index.html`** (~200 KB), không dependency, không CDN — chạy offline được (trừ phần gọi AI/ảnh/TTS Google Dịch).
- Gọi AI: `fetch` + SSE streaming tới endpoint tương thích OpenAI của agent Rice Field (không gửi kèm khoá/header xác thực).
- Ảnh: canvas upscale nhiều bước + `toBlob` → lưu `Blob` vào IndexedDB.
- Không có bộ lọc nội dung nào được thêm ở phía Rice Field AI; nội dung bạn thấy phụ thuộc chính sách của nhà cung cấp hạ tầng miễn phí phía sau agent.
