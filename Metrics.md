# Phase 0 — Chốt phạm vi

- **1. Dự án:** Thiết bị đo đường huyết không xâm lấn sử dụng NIR + AI, kết hợp với ứng dụng để hiển thị và lưu kết quả đo.

- **2. Persona:** Người trưởng thành có nhu cầu tự theo dõi đường huyết tại nhà.

- **3. Core job:** "Tôi muốn biết mức đường huyết của mình tại thời điểm cần kiểm tra và theo dõi sự thay đổi của nó theo thời gian mà không phải lấy máu mỗi lần đo."
# 01 — Core Action

## 1. Phân biệt bốn khái niệm

| Khái niệm | Câu trả lời |
| :--- | :--- |
| **Core job** | Biết được mức đường huyết của bản thân tại thời điểm cần kiểm tra và theo dõi sự thay đổi theo thời gian mà không phải lấy máu mỗi lần đo. |
| **Core action** | Đặt ngón tay vào thiết bị và thực hiện một lần đo đường huyết. |
| **Core value** | Biết được mức đường huyết của bản thân tại thời điểm đo và có thêm dữ liệu để theo dõi sự thay đổi theo thời gian. |
| **Core value event** | `measurement_completed` — lần đo hoàn tất và hệ thống trả về kết quả đường huyết cho người dùng. |

### Phân biệt Core Action và Core Value Event

**Core action** là hành vi do người dùng thực hiện:

> Đặt ngón tay vào thiết bị và thực hiện phép đo.

**Core value event** là sự kiện xác nhận rằng hành vi đó đã tạo ra giá trị:

> Hệ thống hoàn thành phép đo và trả kết quả đường huyết cho người dùng.

Vì vậy, hai khái niệm này có liên quan nhưng không hoàn toàn giống nhau.

---

## 2. Core Action Card

| Thành phần | Câu trả lời của tôi |
| :--- | :--- |
| **Target user** | Người trưởng thành có nhu cầu tự theo dõi đường huyết tại nhà. |
| **Core job** | Biết được mức đường huyết của bản thân tại thời điểm cần kiểm tra và theo dõi sự thay đổi theo thời gian mà không phải lấy máu mỗi lần đo. |
| **Core action** | Đặt ngón tay vào thiết bị và thực hiện một lần đo đường huyết. |
| **Object** | Một phiên đo đường huyết của người dùng. |
| **Preconditions** | Thiết bị đã sẵn sàng, ứng dụng đã kết nối với thiết bị và người dùng đặt ngón tay đúng vị trí đo. |
| **Completion rule** | Người dùng thực hiện phép đo và hệ thống thu được tín hiệu hợp lệ để hoàn thành quá trình đo. |
| **Core value** | Người dùng biết được mức đường huyết tại thời điểm đo và có thêm dữ liệu để theo dõi theo thời gian. |
| **Evidence of value** | Kết quả đường huyết được trả về và người dùng có thể xem kết quả trên ứng dụng. |
| **Candidate event** | `measurement_completed` |

---

## 3. Tự kiểm Core Action

### 1. Gần core value — PASS

Hành vi thực hiện phép đo tiến gần trực tiếp đến core value vì nếu không có phép đo thì người dùng không thể nhận được thông tin về mức đường huyết.

### 2. Có thể lặp lại — PASS

Người dùng có thể thực hiện nhiều lần đo khác nhau khi phát sinh nhu cầu theo dõi đường huyết.

### 3. Có thể quan sát — PASS

Có thể xác định rõ thời điểm bắt đầu và kết thúc một phiên đo thông qua quá trình thiết bị thu tín hiệu và hoàn thành phép đo.

### 4. Có ý nghĩa — PASS

Số lần đo hoàn thành tăng có thể phản ánh người dùng đang thực sự sử dụng chức năng tạo ra giá trị cốt lõi của sản phẩm, khác với việc chỉ mở ứng dụng.

### 5. Có thể tác động — PASS

Team có thể cải thiện khả năng người dùng hoàn thành phép đo bằng cách:

- Rút ngắn thời gian đo.
- Cải thiện độ ổn định của tín hiệu.
- Hướng dẫn người dùng đặt ngón tay đúng vị trí.
- Cải thiện giao diện và phản hồi trong quá trình đo.
- Giảm tỷ lệ đo thất bại.

### Kết quả tự kiểm

> **5/5 tiêu chí — PASS**

Core action được giữ lại.

---

## 4. Kết luận Core Action

> **Core Action của sản phẩm là: Đặt ngón tay vào thiết bị và thực hiện một lần đo đường huyết.**

Hành vi này được chọn vì nó trực tiếp phục vụ core job, có thể lặp lại khi nhu cầu theo dõi quay lại, có thể quan sát và đo lường được, đồng thời team có thể tác động để tăng tỷ lệ người dùng hoàn thành phép đo.

> **Core Value Event:** `measurement_completed`

Event này xác nhận rằng một lần đo đã hoàn tất và người dùng đã có kết quả để sử dụng.

# 02 — Nature & cadence

## 1. Action Nature Card

| Thành phần | Câu trả lời của tôi |
| :--- | :--- |
| **Actor** | Người dùng cá nhân thực hiện hành vi đo đường huyết trên thiết bị. |
| **Intent** | Muốn biết mức đường huyết tại thời điểm cần kiểm tra và có dữ liệu để theo dõi sự thay đổi theo thời gian. |
| **Trigger** | Chủ yếu do user chủ động khi phát sinh nhu cầu theo dõi; ngoài ra có thể xuất hiện sau một sự kiện như bữa ăn, hoạt động thể chất hoặc khi người dùng muốn kiểm tra lại kết quả trước đó. |
| **Effort** | Người dùng cần chuẩn bị thiết bị, đặt ngón tay đúng vị trí và giữ ổn định trong thời gian đo. Effort ở mức thấp đến trung bình vì mỗi lần đo cần một khoảng thời gian và thao tác vật lý. |
| **Value timing** | Value xuất hiện gần như ngay sau khi phép đo hoàn tất và hệ thống trả kết quả. Giá trị theo dõi dài hạn được tích lũy qua nhiều lần đo. |
| **State** | Kết quả đo, thời điểm đo và lịch sử các lần đo được lưu lại để người dùng xem và so sánh theo thời gian. |
| **Dependency** | Phụ thuộc vào thiết bị hoạt động bình thường, tín hiệu đo đủ chất lượng và người dùng đặt ngón tay đúng vị trí. |
| **Repeat condition** | Action xuất hiện lại khi người dùng có nhu cầu kiểm tra hoặc theo dõi đường huyết tiếp theo, ví dụ muốn kiểm tra sau một khoảng thời gian, sau bữa ăn hoặc muốn so sánh với kết quả trước đó. |

---

## 2. Phân tích Nature

### Cơ chế xuất hiện của Core Action

Core action **không phải là hành vi có tần suất cố định theo ngày**.

Người dùng không nhất thiết phải thực hiện:

```text
Mỗi ngày
   ↓
Mở app
   ↓
Đo đường huyết
```

# 03 — Metric System

## 1. Activation Metric

### Start event

> `first_measurement_started` — user bắt đầu thực hiện lần đo đầu tiên.

Đây là thời điểm user thực sự bắt đầu chạm vào core workflow, thay vì chỉ mở ứng dụng hoặc đăng nhập.

### Activation event

> `measurement_completed` — lần đo đầu tiên hoàn thành thành công và user nhận được kết quả đường huyết.

Event này được chọn vì đây là bằng chứng đầu tiên cho thấy user đã thực sự nhận được core value từ sản phẩm.

### Time window

> **Trong cùng một phiên đo / trong vòng 5 phút kể từ `first_measurement_started`.**

User được xem là activated nếu trong vòng 5 phút kể từ khi bắt đầu lần đo đầu tiên, phép đo hoàn tất và có kết quả được trả về.

### Activation Rate

```text
Activation Rate
=
Số user có measurement_completed đầu tiên
/
Số user có first_measurement_started
× 100%
```
# 05 — Product Loop

## 1. Product Loop

### Loop chính: Event-response loop

```text
Natural trigger
(Người dùng có nhu cầu kiểm tra đường huyết)
        ↓
Core action
(Đặt ngón tay vào thiết bị và thực hiện một lần đo)
        ↓
Immediate value
(Nhận kết quả đường huyết tại thời điểm đo)
        ↓
Saved state / investment
(Kết quả được lưu vào lịch sử đo, gắn với thời gian)
        ↓
Next natural trigger
(Người dùng có nhu cầu kiểm tra lại / so sánh với lần trước)
        ↓
Core action tiếp theo
(Thực hiện lần đo tiếp theo)
        ↓
Repeat value
(Nhận kết quả mới và tiếp tục theo dõi xu hướng)
```

### Hai chu kỳ liên tiếp

**Chu kỳ 1**

> Có nhu cầu kiểm tra → thực hiện đo → nhận kết quả → kết quả được lưu vào lịch sử.

**Chu kỳ 2**

> Có nhu cầu kiểm tra lại hoặc theo dõi sự thay đổi → thực hiện đo tiếp → nhận kết quả mới → lịch sử có thêm dữ liệu để so sánh.

### Reason to return

Reason to return không phụ thuộc vào notification hay streak. Người dùng quay lại khi phát sinh **nhu cầu theo dõi hoặc kiểm tra đường huyết tiếp theo**. Kết quả của lần đo trước được lưu lại giúp người dùng có dữ liệu để so sánh với lần đo mới.

### Metric hypothesis

> Nếu loop này hoạt động, metric **Completed Measurements per Active User** sẽ tăng theo hướng **ổn định hơn qua các chu kỳ theo dõi tự nhiên** trong **các tuần tiếp theo**, vì người dùng nhận được giá trị trực tiếp từ mỗi lần đo và có dữ liệu lịch sử để hỗ trợ lần theo dõi tiếp theo.

### Vì sao chọn Event-response loop?

Core action của sản phẩm không nhất thiết xảy ra theo lịch daily cố định. Người dùng đo khi có nhu cầu kiểm tra hoặc theo dõi sự thay đổi đường huyết. Vì vậy, loop được kích hoạt chủ yếu bởi **nhu cầu thực tế của người dùng**, thay vì notification, streak hoặc phần thưởng nhân tạo.

# 06 — Tracking nhanh

## 1. Core Events

| Tên event | Ý nghĩa | Thời điểm ghi nhận | Metric sử dụng |
|---|---|---|---|
| `first_measurement_started` | User bắt đầu phiên đo đầu tiên | Khi hệ thống xác nhận phiên đo đầu tiên đã thực sự bắt đầu | Activation Rate |
| `measurement_started` | User bắt đầu một phiên đo | Khi thiết bị/app xác nhận một phiên đo mới được khởi tạo | Measurement Completion Rate, Time to Result, Invalid Measurement Rate |
| `measurement_completed` | Một lần đo hoàn tất và trả về kết quả hợp lệ, có thể sử dụng | Ngay sau khi hệ thống hoàn tất xử lý và xác nhận kết quả hợp lệ | Activation Rate, Completed Measurements per Active User, Measurement Retention |
| `result_viewed` | User thực sự xem kết quả đo | Khi màn hình kết quả được hiển thị thành công cho user | Result Review Rate |
| `measurement_invalid` | Phiên đo kết thúc nhưng không tạo được kết quả hợp lệ | Khi hệ thống xác nhận phiên đo không hợp lệ | Invalid Measurement Rate |
| `measurement_history_viewed` | User mở lịch sử để xem các kết quả đã lưu | Khi lịch sử đo được tải thành công và hiển thị cho user | Có thể dùng để phân tích hành vi sử dụng lịch sử |

## 2. Event → Metric Mapping

```text
first_measurement_started
        ↓
measurement_completed
        → Activation Rate

measurement_started
        ↓
measurement_completed
        → Measurement Completion Rate
        → Time to Result

measurement_completed
        ↓
measurement_completed (lần tiếp theo)
        → Completed Measurements per Active User
        → Measurement Retention

measurement_completed
        ↓
result_viewed
        → Result Review Rate

measurement_started
        ↓
measurement_invalid
        → Invalid Measurement Rate
```

## 3. Acceptance Criteria

### AC01 — Chỉ ghi completion khi hành vi thật sự hoàn tất

Với mỗi phiên đo, hệ thống chỉ ghi `measurement_completed` khi quá trình đo đã kết thúc và hệ thống xác nhận kết quả hợp lệ, có thể hiển thị cho user. Việc user chỉ bắt đầu đo hoặc bấm nút bắt đầu không được tạo `measurement_completed`.

### AC02 — Không ghi trùng khi reload / retry

Với mỗi `user_id` và `measurement_id`, hệ thống chỉ ghi một event `measurement_completed` cho một lần đo hợp lệ. Reload app, mở lại màn hình hoặc retry request không được tạo thêm event completion cho cùng một lần đo.

### AC03 — Event phản ánh trạng thái đã xảy ra

`measurement_invalid` chỉ được ghi khi hệ thống thực sự xác nhận phiên đo không tạo được kết quả hợp lệ; không ghi event chỉ vì user có ý định đo hoặc thoát khỏi màn hình trước khi hệ thống xác định trạng thái cuối cùng.

## 4. Nguyên tắc Tracking

- Chỉ tracking các event có thể map về một metric hoặc dùng để kiểm tra chất lượng của metric.
- Ưu tiên event phản ánh **trạng thái đã xảy ra**, không phải ý định của user.
- `measurement_completed` là event quan trọng nhất vì đại diện cho value event của sản phẩm.
- Không dùng số lần mở app hoặc số lần click nút đo làm thay thế cho số lần đo hoàn thành.