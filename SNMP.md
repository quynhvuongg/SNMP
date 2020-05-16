# Simple Network Management Protocol

![image](https://user-images.githubusercontent.com/61721493/82122895-88089400-97c0-11ea-9779-8f7a51b62890.png)


## Giới thiệu chung về SNMP
-  SNMP - Giao thức quản lý mạng đơn giản là tập hợp các giao thức dùng để quản lý mạng, nó được thiết kế để chạy trên nền TCP/IP và quản lý các thiết bị có nối mạng TCP/IP.
- SNMP là một giao thức lớp ứng dụng sử dụng số cổng UDP 161 / 162. Các thiết bị mạng không nhất thiết phải là máy tính mà có thể là switch, router, firewall, adsl gateway, và cả một số phần mềm cho phép quản trị bằng SNMP.
-  SNMP là giao thức đơn giản, do nó được thiết kế đơn giản trong cấu trúc bản tin và thủ tục hoạt động, và còn đơn giản trong bảo mật (ngoại trừ SNMP version 3). Sử dụng phần mềm SNMP, người quản trị mạng có thể quản lý, giám sát tập trung từ xa toàn mạng của mình.

## Các thành phần SNMP

![image](https://user-images.githubusercontent.com/61721493/82123766-4d552a80-97c5-11ea-8983-314fc2f0b105.png)

**_SNMP Manager_**

 Một hệ thống tập trung được sử dụng để giám sát mạng,nó còn được gọi là trạm quản lý mạng (NMS) thường là một máy tính được sử dụng để chạy một hoặc nhiều hệ thống quản lý mạng.

Chức năng chính:
-  Truy vấn agents
- Nhận phản hồi từ agents
-  Set biến trong agents
- Công nhận các sự kiện không đồng bộ từ các đại lý

**_SNMP Agent_**

Agent là một nút mạng hỗ trợ giao thức SNMP và thuộc về mạng bị quản lí, có nhiệm vụ thu thập thông tin quản lí và lưu trữ để phục vụ cho hệ thống quản lí mạng. Những thiết bị chịu sự quản lí, đôi khi được gọi là những phần tử mạng, có thể là các bộ định tuyến và máy chủ truy nhập (Access Server), switch và bridge, hub, máy tính hay là máy in trong mạng.

Chức năng chính:
- Thu thập thông tin quản lý về các thiết bị.
- Lưu trữ và truy xuất thông tin quản lý như được xác định trong MIB.
- Cảnh báo một sự kiện cho người quản lý.

**_Management Information Base_**

- MIB bao gồm thông tin về các tài nguyên sẽ được quản lý. Những thông tin này được tổ chức theo thứ bậc được xác định bằng định danh đối tượng (OID).
- MIB có thể lưu trữ trong file (MIB file) và có thể biểu diễn thành MIB tree. MIB có thể được chuẩn hóa hoặc tự tạo.

![image](https://user-images.githubusercontent.com/61721493/82125252-da50b180-97ce-11ea-8484-3cfb909882e6.png)

## Các phương thức hoạt động 

|Bản tin/Phương thức  | Mô tả |
|--|--|
| GET | Bản tin yêu cầu được gửi bởi manager đến agent để lấy một hoặc nhiều giá trị từ thiết bị được quản lý dựa trên OIDs  |
| GETNEXT | Cho phép manager yêu cầu đối tượng tiếp theo trong MIB. Đây là một cách mà bạn có thể duyệt qua cấu trúc của MIB mà không phải lo lắng về những gì OID cần truy vấn.  | 
| SET | Được gửi bởi manager đến agent để thay đổi giá trị được giữ bởi một biến trên agent, có thể được sử dụng để kiểm soát thông tin cấu hình hoặc sửa đổi trạng thái của máy chủ từ xa. |
| GETBULK  | tương tự như  GETNEXT ngoại trừ vấn đề liên quan tới số lượng dữ liệu được lấy ra, nó cho phép agent gửi lại manager dữ liệu liên quan tới nhiều đối tượng thay vì từng đối tượng bị quản lí. GETBULK có thể giảm bớt lưu lượng truyền dẫn và các bản tin đáp ứng thông báo về các điều kiện vi phạm |
| RESPONSE | Bản tin được gửi bởi agent tới manager được dùng để phản hồi lại yêu cầu GET/SET ở trên |
| TRAP  | Bản tin do agent tự động gửi tới manager khi có sự kiện xảy ra đối với một object nào đó. |
| INFORM  | Để xác nhận việc nhận TRAP, manager sẽ gửi bản tin này cho agent. Nếu agent không nhận được  bản tin này, nó có thể tiếp tục gửi lại TRAP. |

## Các phiên bản 

|Version  |  |
|--|--|
| SNMPv1  | Đây là phiên bản đầu tiên của giao thức SNMP, được xác định trong RFC 1155 và 1157, sử dụng community string để xác thực và chỉ sử dụng UDP.  |
| SNMPv2c  | Giao thức cải tiến từ SNMPv1 được định nghĩa trong RFC 1901, RFC 1905, RFC 1906, RFC 2578, sử dụng community string để xác thực .Ngoài sử dụng UDP  nó có thể được cấu hình để sử dụng TCP.  |
| SNMPv3  | Phiên bản cải tiến nhiều về phần an toàn, sử dụng MAC dựa trên Hash với MD5 hoặc SHA để xác thực và DES-56 cho quyền riêng tư. Phiên bản này sử dụng TCP. |

**_SNMP security levels_** : Sử dụng trong SNMPv3
- NoAuthNoPriv: Mức bảo mật này (không xác thực, không bảo mật) sử dụng community string để xác thực và không mã hóa cho quyền riêng tư.
- AuthNoPriv: Mức bảo mật này (xác thực, không có quyền riêng tư) sử dụng HMAC với MD5 để xác thực và không sử dụng mã hóa cho quyền riêng tư.
- AuthPriv: Mức bảo mật này (xác thực, bảo mật) sử dụng HMAC với MD5 hoặc SHA để xác thực và mã hóa sử dụng thuật toán DES-56.



