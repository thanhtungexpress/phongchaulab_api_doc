# API NHẬN KẾT QUẢ TỪ LIS
## API Get Token:
- Endpoint: [http://api-url/gettoken](http://api-url/gettoken)
- Method: GET
- Response JSON: {"token": "my_token"}

**Note:**
> *Mã TOKEN sẽ hết hạn sau một giờ. Nếu hết hạn, vui lòng GET lại token.*
  
**Response example**
> {
    "token": "eyJhbGciOiJBMTI4Q0JDLUhTMjU2IiwidHlwIjoiSldUIiwia2lkIjoicW8zRTlISVE1SWh0N2U4dktoRzJtc1hhNHJNVUFrTUQifQ.eyJ1c2VybmFtZSI6InBob25nY2hhdWxhYl9hcGkiLCJyb2xlIjoiYWRtaW4iLCJuYmYiOjE3MDU0NjI3MjQsImV4cCI6MTcwNTQ2NjMyNCwiaXNzIjoicGhvbmdjaGF1bGFiX2FwaSIsImF1ZCI6ImFwaSJ9.Q0BXPB72ex7WbFU-AgvsEzgK9NZ6IMubrVepwOSUdus"
}
## API Post Result:
- Endpoint: [http://api-url/saveresultdata](http://api-url/saveresultdata)
- Method: POST
- Header:
    Authorization: Bearer my_token 
- Body JSON: {}
- Response JSON: { Success = true/false, Message = "Message" }
  
**Note:**
>  *Success: true -> Lưu thành công; else: Lưu thất bại*
> 
> *Message: Mô tả của response*
  
**POST result example**
> curl -X POST -H "Content-Type: application/json" -H "Authorization: Bearer my_token" -d '{
  "SampleId": "123",
  "Stt": "1",
  "NgayChidinh": "2024-01-14T10:00:00",
  "MaBenhNhan": "BN001",
  "SoBienLai": "BL001",
  "TenBenhNhan": "John Doe",
  "DiaChi": "123 Main Street",
  "NamSinh": 1990,
  "GioiTinh": "Male",
  "ChanDoan": "Fever",
  "TenDoiTuong": "Insurance",
  "TenNoiChidinh": "Lab Center",
  "TenBacSi": "Dr. Smith",
  "Email": "john.doe@example.com",
  "DienThoai": "123456789",
  "ThoiGianLayMau": "2024-01-14T09:30:00",
  "UserI": "user123",
  "InTime": "2024-01-14T11:00:00",
  "Pdfresult": "",
  "KetQua": [
    {
      "MaxetNghiem": "XN001",
      "TenXetNghiem": "Blood Test",
      "KetQua": "Normal",
      "ChiSoBinhThong": "123",
      "DonVi": "mg/dL",
      "BatThuong": false,
      "TenNhomXN": "General",
      "ThuTuNhomXN": 1,
      "ThuTuSapXep": 1,
      "InDam": true,
      "InDamKetQua": false,
      "XetNghiemChinh": true,
      "FontSize": 12,
      "UserUpdate": "user123",
      "DateUpdate": "2024-01-14T12:30:00"
    },
    {
      "MaxetNghiem": "XN002",
      "TenXetNghiem": "Blood Test2",
      "KetQua": "Normal",
      "ChiSoBinhThong": "124",
      "DonVi": "mg/dL",
      "BatThuong": false,
      "TenNhomXN": "General",
      "ThuTuNhomXN": 1,
      "ThuTuSapXep": 1,
      "InDam": true,
      "InDamKetQua": false,
      "XetNghiemChinh": true,
      "FontSize": 12,
      "UserUpdate": "user123",
      "DateUpdate": "2024-01-14T12:30:00"
    }
  ]
}' http://api-url/saveresultdata


## Mô tả các trường
### Bệnh nhân
```sql
Sampleid varchar(30) --(Mẫu ID): ID của mẫu bệnh phẩm.
Stt varchar(10) --(Số Thứ Tự): Số thứ tự của bệnh nhân.
Ngaychidinh datetime --(Ngày Chỉ Định): Ngày bác sĩ chỉ định.
Mabenhnhan varchar(30) --(Mã Bệnh Nhân): Mã định danh của bệnh nhân.
Sobienlai varchar(30) --(Số Biên Lai): Số biên lai thanh toán.
Tenbenhnhan nvarchar(255) --(Tên Bệnh Nhân): Tên đầy đủ của bệnh nhân.
Diachi nvarchar(512) --(Địa Chỉ): Địa chỉ cư trú của bệnh nhân.
Namsinh int --(Năm Sinh): Năm sinh của bệnh nhân.
Gioitinh nvarchar(10) --(Giới Tính): Giới tính của bệnh nhân.
Chandoan nvarchar(512) --(Chẩn Đoán): Chẩn đoán ban đầu.
Tendoituong nvarchar(50) --(Tên Đối Tượng): Tên đối tượng bảo hiểm y tế.
Tennoichidinh nvarchar(255) --(Tên Nơi Chỉ Định): Tên nơi bác sĩ chỉ định.
Tenbacsi nvarchar(255) --(Tên Bác Sĩ): Tên bác sĩ chỉ định.
Email nvarchar(255) --(Email): Địa chỉ email của bệnh nhân.
Dienthoai varchar(15) --(Điện Thoại): Số điện thoại của bệnh nhân.
Thoigianlaymau datetime --(Thời Gian Lấy Mẫu): Thời gian lấy mẫu từ bệnh nhân.
Useri varchar(30) --(Người Dùng): Người dùng thực hiện thao tác.
Intime datetime --(Thời Gian Nhận Lệnh): Thời gian nhận lệnh.
Pdfresult varbinary(MAX) --(Kết Quả PDF): Kết quả được xuất ra dưới định dạng PDF.
```
### Kết quả
```sql
Sampleid varchar(30) --(Mẫu ID): ID của mẫu bệnh phẩm.
Maxetnghiem varchar(30) --(Mã Xét Nghiệm): Mã xét nghiệm của kết quả.
Tenxetnghiem nvarchar(255) --(Tên Xét Nghiệm): Tên xét nghiệm tương ứng.
Ketqua nvarchar(255) --(Kết Quả): Giá trị kết quả xét nghiệm.
Chisobinhthong nvarchar(50) --(Chỉ Số Bình Thường): Chỉ số so sánh với giá trị bình thường.
Donvi nvarchar(50) --(Đơn Vị): Đơn vị đo lường của kết quả.
Batthuong bit (boolean) --(Bất Thường): Thông tin về kết quả có bất thường hay không.
Tennhomxn nvarchar(50) --(Tên Nhóm XN): Tên nhóm xét nghiệm.
Thutunhomxn int --(Thứ Tự Nhóm XN): Thứ tự của nhóm xét nghiệm.
Thutusapxep int --(Thứ Tự Sắp Xếp): Thứ tự sắp xếp kết quả.
Indam bit (boolean) --(In Đậm): Trạng thái in đậm của kết quả.
Indamketqua bit (boolean) --(In Đậm Kết Quả): Trạng thái in đậm của giá trị kết quả.
Xetnghiemchinh bit (boolean) --(Xét Nghiệm Chính): Trạng thái xác định xét nghiệm là chính hay không.
Fontsize int --(Kích Thước Font): Kích thước font chữ sử dụng cho kết quả xét nghiệm.
Userupdate varchar(30) --(Người Cập Nhật): Người dùng thực hiện cập nhật kết quả.
Dateupdate datetime --(Ngày Cập Nhật): Ngày và giờ khi kết quả xét nghiệm được cập nhật.
```
### Model
```c#
    public class ResultDataModel
    {
        public string SampleId { get; set; }
        public string Stt { get; set; }
        public DateTime NgayChidinh { get; set; }
        public string MaBenhNhan { get; set; }
        public string SoBienLai { get; set; }
        public string TenBenhNhan { get; set; }
        public string DiaChi { get; set; }
        public int NamSinh { get; set; }
        public string GioiTinh { get; set; }
        public string ChanDoan { get; set; }
        public string TenDoiTuong { get; set; }
        public string TenNoiChidinh { get; set; }
        public string TenBacSi { get; set; }
        public string Email { get; set; }
        public string DienThoai { get; set; }
        public DateTime ThoiGianLayMau { get; set; }
        public string UserI { get; set; }
        public DateTime InTime { get; set; }
        public byte[]? Pdfresult { get; set; }
        public List<ResultDataModelKetQua> KetQua { get; set; }
    }
    public class ResultDataModelKetQua
    {
        public string MaxetNghiem { get; set; }
        public string TenXetNghiem { get; set; }
        public string KetQua { get; set; }
        public string ChiSoBinhThong { get; set; }
        public string DonVi { get; set; }
        public bool BatThuong { get; set; }
        public string TenNhomXN { get; set; }
        public int ThuTuNhomXN { get; set; }
        public int ThuTuSapXep { get; set; }
        public bool InDam { get; set; }
        public bool InDamKetQua { get; set; }
        public bool XetNghiemChinh { get; set; }
        public byte FontSize { get; set; }
        public string UserUpdate { get; set; }
        public DateTime DateUpdate { get; set; }
    }
```
