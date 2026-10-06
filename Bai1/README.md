PHÂN TÍCH LỖI
Lỗi 1: Điều phối xe sai quy tắc FIFO
Đoạn mã:
const nextVehicle = waitingQueue.pop();
=> pop() lấy phần tử cuối mảng nên xe đến sau cùng sẽ được vào sạc trước.

Cách sửa:
const nextVehicle = waitingQueue.shift();
=> shift() lấy phần tử đầu mảng, đúng với xe đến trước được phục vụ trước.

Lỗi 2: Vượt quá chỉ số mảng
Đoạn mã:

for (let i = 0; i <= completedSessionsKwh.length; i++)

Khi i = completedSessionsKwh.length, chương trình truy cập: completedSessionsKwh[4]
Giá trị nhận được là: undefined
Khi cộng: totalKwh += undefined => NaN

Cách sửa:
for (let i = 0; i < completedSessionsKwh.length; i++)


TEST CASES
Trường hợp kiểm thử	Dữ liệu đầu vào	Kết quả sai thực tế	Kết quả đúng mong đợi
TC01 - Hàng đợi 3 xe	['29A-112.33', '30E-889.12', '51K-678.99']	Điều phối 51K-678.99 vào sạc trước	Điều phối 29A-112.33 vào sạc trước
TC02 - Tính tổng điện năng	[45.2, 30.5, 62.8, 28.0]	Tổng sản lượng = NaN, doanh thu = NaN	Tổng sản lượng = 166.5 kWh, doanh thu = 749250 VNĐ