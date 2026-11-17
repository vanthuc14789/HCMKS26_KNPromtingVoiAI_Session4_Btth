---


---

<h1 id="bài-tập-thực-hành-tổng-hợp-–-session-04"><strong>BÀI TẬP THỰC HÀNH TỔNG HỢP – SESSION 04</strong></h1>
<p><strong>Chủ đề: Kỹ thuật Prompting Nâng cao (Logic &amp; Chuỗi)</strong></p>
<h2 id="thiết-kế-giải-pháp"><strong>1. Thiết kế giải pháp</strong></h2>
<p><strong>Tên giải pháp:</strong> Tự động hóa quy trình kiểm tra và xử lý đơn hàng tại cửa hàng.</p>
<p><strong>Mục tiêu:</strong> Sử dụng AI để kiểm tra thông tin, tính tiền, phân loại đơn hàng và phát hiện dữ liệu sai lệch.</p>
<p><strong>Input (Đầu vào):</strong></p>
<ul>
<li>
<p>Mã đơn hàng.</p>
</li>
<li>
<p>Tên khách hàng.</p>
</li>
<li>
<p>Tên sản phẩm.</p>
</li>
<li>
<p>Số lượng.</p>
</li>
<li>
<p>Đơn giá.</p>
</li>
<li>
<p>Địa chỉ giao hàng.</p>
</li>
<li>
<p>Số điện thoại.</p>
</li>
</ul>
<p><strong>Output (Đầu ra):</strong></p>
<ul>
<li>
<p>Thông tin đơn hàng đã kiểm tra.</p>
</li>
<li>
<p>Tổng tiền cần thanh toán.</p>
</li>
<li>
<p>Trạng thái đơn hàng.</p>
</li>
<li>
<p>Lỗi phát hiện.</p>
</li>
<li>
<p>Hướng xử lý.</p>
</li>
</ul>
<h2 id="thiết-kế-chuỗi-prompt-chaining"><strong>2. Thiết kế chuỗi Prompt Chaining</strong></h2>
<p>Quy trình gồm 4 bước liên kết:</p>
<p><strong>Bước 1: Kiểm tra dữ liệu</strong></p>
<p>Phát hiện thông tin thiếu hoặc sai.</p>
<p><strong>Bước 2: Tính toán</strong></p>
<p>Tính tổng tiền nếu dữ liệu hợp lệ.</p>
<p><strong>Bước 3: Phân loại</strong></p>
<p>Xác định trạng thái đơn hàng.</p>
<p><strong>Bước 4: Tổng hợp kết quả</strong></p>
<p>Xuất báo cáo và hướng xử lý.</p>
<h2 id="prompt-hệ-thống-và-các-bước-thực-thi"><strong>3. Prompt hệ thống và các bước thực thi</strong></h2>
<h3 id="prompt-1-kiểm-tra-dữ-liệu"><strong>Prompt 1: Kiểm tra dữ liệu</strong></h3>
<p>Bạn là AI kiểm tra đơn hàng. Hãy kiểm tra mã đơn, tên khách hàng, sản phẩm, số lượng, đơn giá, địa chỉ và số điện thoại.</p>
<ul>
<li>
<p>Nếu thiếu thông tin, ghi rõ thông tin còn thiếu.</p>
</li>
<li>
<p>Nếu số lượng nhỏ hơn hoặc bằng 0 hoặc đơn giá âm, báo dữ liệu không hợp lệ.</p>
</li>
<li>
<p>Không tự ý tạo dữ liệu.</p>
</li>
<li>
<p>Chỉ chuyển dữ liệu hợp lệ sang bước tiếp theo.</p>
</li>
</ul>
<h3 id="prompt-2-tính-toán-đơn-hàng"><strong>Prompt 2: Tính toán đơn hàng</strong></h3>
<p>Dựa trên dữ liệu đã kiểm tra ở bước 1:</p>
<ul>
<li>
<p>Tính tổng tiền = Số lượng × Đơn giá.</p>
</li>
<li>
<p>Kiểm tra lại kết quả.</p>
</li>
<li>
<p>Nếu dữ liệu không hợp lệ, không thực hiện tính toán.</p>
</li>
<li>
<p>Chuyển kết quả sang bước phân loại.</p>
</li>
</ul>
<h3 id="prompt-3-phân-loại-đơn-hàng"><strong>Prompt 3: Phân loại đơn hàng</strong></h3>
<p>Dựa trên kết quả bước 1 và bước 2, phân loại đơn hàng:</p>
<ul>
<li>
<p>Hợp lệ: Đầy đủ thông tin và dữ liệu chính xác.</p>
</li>
<li>
<p>Cần bổ sung: Thiếu thông tin.</p>
</li>
<li>
<p>Cần kiểm tra: Dữ liệu sai hoặc mâu thuẫn.</p>
</li>
</ul>
<p>Không kết luận đơn hàng hợp lệ nếu còn lỗi.</p>
<h3 id="prompt-4-tổng-hợp-kết-quả"><strong>Prompt 4: Tổng hợp kết quả</strong></h3>
<p>Tổng hợp kết quả từ 3 bước trước theo định dạng:</p>
<ul>
<li>
<p>Mã đơn hàng:</p>
</li>
<li>
<p>Tên khách hàng:</p>
</li>
<li>
<p>Sản phẩm:</p>
</li>
<li>
<p>Số lượng:</p>
</li>
<li>
<p>Đơn giá:</p>
</li>
<li>
<p>Tổng tiền:</p>
</li>
<li>
<p>Trạng thái:</p>
</li>
<li>
<p>Lỗi phát hiện:</p>
</li>
<li>
<p>Hướng xử lý:</p>
</li>
</ul>
<p>Nếu quá trình bị gián đoạn, sử dụng kết quả đã hoàn thành để tiếp tục từ bước chưa xử lý. Không tự tạo dữ liệu bị mất.</p>
<h2 id="cơ-chế-xử-lý-lỗi"><strong>4. Cơ chế xử lý lỗi</strong></h2>
<ul>
<li>
<p>Dữ liệu bị trống: Yêu cầu bổ sung.</p>
</li>
<li>
<p>Số lượng âm hoặc bằng 0: Báo lỗi.</p>
</li>
<li>
<p>Đơn giá âm: Không thực hiện tính tiền.</p>
</li>
<li>
<p>Số điện thoại sai định dạng: Yêu cầu kiểm tra.</p>
</li>
<li>
<p>Dữ liệu mâu thuẫn: Yêu cầu xác nhận.</p>
</li>
<li>
<p>AI bị ngắt giữa chừng: Tiếp tục từ bước chưa hoàn thành dựa trên dữ liệu đã lưu.</p>
</li>
</ul>
<h2 id="kết-quả-chạy-thử"><strong>5. Kết quả chạy thử</strong></h2>
<p><strong>Dữ liệu đầu vào:</strong></p>
<ul>
<li>
<p>Mã đơn: DH001</p>
</li>
<li>
<p>Khách hàng: Nguyễn Văn A</p>
</li>
<li>
<p>Sản phẩm: Chuột máy tính</p>
</li>
<li>
<p>Số lượng: 2</p>
</li>
<li>
<p>Đơn giá: 150.000 VNĐ</p>
</li>
<li>
<p>Địa chỉ: TP. Hồ Chí Minh</p>
</li>
<li>
<p>Số điện thoại: 0901234567</p>
</li>
</ul>
<p><strong>Kết quả đầu ra của AI:</strong></p>
<h1 id="báo-cáo-xử-lý-đơn-hàng">BÁO CÁO XỬ LÝ ĐƠN HÀNG</h1>
<ul>
<li>
<p>Mã đơn hàng: DH001</p>
</li>
<li>
<p>Tên khách hàng: Nguyễn Văn A</p>
</li>
<li>
<p>Sản phẩm: Chuột máy tính</p>
</li>
<li>
<p>Số lượng: 2</p>
</li>
<li>
<p>Đơn giá: 150.000 VNĐ</p>
</li>
<li>
<p>Tổng tiền: 300.000 VNĐ</p>
</li>
<li>
<p>Trạng thái: Hợp lệ</p>
</li>
<li>
<p>Lỗi phát hiện: Không có.</p>
</li>
<li>
<p>Hướng xử lý: Chuyển sang bước chuẩn bị giao hàng.</p>
</li>
</ul>
<p><strong>Kết luận:</strong> Đơn hàng có đầy đủ thông tin, dữ liệu hợp lệ và tính toán chính xác.</p>

