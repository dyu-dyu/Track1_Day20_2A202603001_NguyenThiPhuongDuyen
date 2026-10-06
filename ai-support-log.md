# AI Support Log

## AI đã giúp tôi ở đâu?

AI hỗ trợ brainstorm các ứng viên core action, đặt câu hỏi phản biện, gợi ý cách phân biệt Core Action với Value Event, gợi ý tên event dạng `object_action` và acceptance criteria cho phần tracking.

## AI sai, hời hợt hoặc đề xuất metric sai nature ở đâu?

Ban đầu AI có xu hướng đề xuất retention theo D7/D30 và các chỉ số mang tính daily habit. Điều này chưa phù hợp với nature của sản phẩm vì hành vi đo đường huyết mang tính periodic + event-driven, không phải daily habit cố định.

## Tôi đã tự sửa hoặc quyết định lại điều gì?

Tôi tự quyết định Core Action là **“Đặt ngón tay vào thiết bị và thực hiện một lần đo đường huyết”**, không dùng `measurement_completed` làm Core Action. Tôi cũng quyết định retention phải dựa trên việc user quay lại thực hiện lần đo tiếp theo theo chu kỳ tự nhiên, thay vì ép theo D7/D30. Product Loop được chọn là **event-response loop** vì reason to return đến từ nhu cầu kiểm tra đường huyết tiếp theo, không phải notification hoặc streak.

## Nội dung này có hữu ích không?

Có. AI hữu ích ở phần brainstorm và phản biện, nhưng các quyết định cuối cùng về core action, cadence, metric và rationale được tôi tự kiểm tra và quyết định dựa trên nature của sản phẩm.