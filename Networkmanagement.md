# Network management

## Outline

Quản lý mạng

Phần 1: Tổng quan về mạng

1. Giới thiệu chung về mạng
2. Kiến trúc mạng

Phần 2: Quản lý mạng

1. Giới thiệu chung về quản lý mạng
2. Kiến trúc quản lý mạng
3. Các giao thức quản lý mạng
4. Một số thách thức trong quản lý mạng

## Phần 3: SNMP

---

## Introduction of Network Management

network management involves the planning, organizing, monitoring, accounting, and controlling of activities and resources and to keep the network service available and correct.

objectives of network management:

- Managing system resources and services: this includes control, monitor, update, and report of system states, device configurations, and network services.
- Simplifying systems management complexity: is the task of management systems that extrapolates systems management information into a humanly manageable form. Conversely, management systems should also have the ability to interpret high-level management objectives.
- Providing reliable services: means to provide networks with a high quality of service and to minimize system downtime. Distributed management systems should detect and fix network faults and errors. Network management must safeguard against all security threats.
- Maintaining cost consciousness: requires to keep track of system resources and network users. All network resource and service usage should be tracked and reported.

## Components of NM system

Network management has three main components: a managing center, a managed device, and a network management protocol.

- The managing center consists of the network administrator and his or her facilities.
- A managed device is the network equipment, including its software, that is controlled by the managing center. Any hub, bridge, router, server, printer or modem can be a managed device.
- The network management protocol is a policy between the managing center and the managed devices. The protocol in this context allows the managing center to obtain the status of managed devices.

As specified in Internet RFCs and other documents, a typical distributed
management system comprises:
• Network elements: Equipments which communicate with the network, according to standards defined by the ITU-T, with the purpose of being monitored or controlled, are named network elements. Sometimes they are also called managed devices [ITU96]. Network elements are hardware devices such as computers, routers, and terminal servers that are connected to networks. A network element is a network node that contains an SNMP agent, which resides on a managed network.
• Manager: A manager generates commands and receives notifications from agents. There are usually only a few managers in a system.
• Agents: Agents collect and store management information such as the number of error packets received by a network element. An agent has local knowledge of management information and transforms that information into the form compatible with SNMP. An agent responds to commands from the manager and sends notification to the manager. There are potentially many agents in a system.
• Managed object: A managed object is a vision of a feature of a network, from the point of view of the management system [ITU92]. All physical and logical resources, such as signaling terminals, routes, event
logs, alarm reports and subscriber data, are regarded as managed objects. For example, in IP networks, a list of current active TCP circuits in a particular host computer is a managed object. Managed objects
differ from variables, which are particular object instances. Managed objects can be scalar (defining a single object instance) or tabular (defining multiple and related instances). In literature, “managed object” is sometimes used interchangeably with “managed element.”
• Network Management Stations (NMSs): Sometimes NMSs are called consoles. These devices execute management applications that monitor and control network elements. Physically, NMSs are usually engineering workstation-caliber computers with fast CPUs, mega pixel color displays, substantial memory, and abundant disk space. At least one NMS must be present in each managed environment.
• Structure of Management Information (SMI)
The structure of management information (SMI) language is used to define the rules for naming objects and to encode objects in a managed network center. In other words, SMI is a language by which a specific
instance of the data in a managed network center is defined. SMI subdivides into three parts: module definitions, object definitions, and notification definitions. Module definitions are used when describing information modules. An ASN.1 macro, MODULE-IDENTITY, is used to concisely convey the
semantics of an information module. Object definitions describe managed objects.
An ASN.1 macro, OBJECT-TYPE, is used to concisely convey the syntax and semantics
of a managed object.
Notification definitions (also known as “traps”) are used when describing unsolicited transmissions of management information. An ASN.1 macro, NOTIFICATION-TYPE, concisely conveys the syntax and semantics of
a notification.
• Management Information Base (MIB)
A management information base (MIB) stems from the OSI/ISO Network management model and is a type of database used to manage the devices in a communications network. It comprises a collection of objects in a (virtual) database used to manage entities (such as routers and switches) in a network.

With the expansion of networks, the evolution of network architectures, and the increasing requirements for network management, the network management protocols also evolve consequently. A typical management network system will make use of the management operation services to monitor network elements. Management agents found
on network elements will make use of the management notification services to send notifications or alarms to the network management system.
• Network management protocols are used to define how network management information is exchanged between network management services and management agents. Some popular network management protocols are discussed as follows.

## Network Management Architectures

(48)

## Simple Network Management Protocol (SNMP)

The SNMP is an application layer protocol and uses User Datagram Protocol (UDP) to exchange management information between management entities, which offers network management services for monitoring and control of network devices. SNMP
enables network administrators to manage network performance, find and solve network problems, and plan for network growth. SNMP is a network management tool that allows network administrator to perform monitoring control, and planning tasks on the network to be managed.

---

Quản lý mạng bao gồm các nhiệm vụ: Lên kế hoạch, tổ chức, giám sát, tính toán và điều khiển các hoạt động và các tài nguyên mạng giữ cho các dịch vụ mạng luôn sẵn sàng và thực hiện đúng nhiệm vụ của mình.
Mục tiêu của quản lý mạng:
•	Quản lý tài nguyên và dịch vụ: Bao gồm việc điều khiển, giám sát, cập nhật và báo cáo tình trạng mạng, cấu hình thiết bị và dịch vụ mạng.
•	Đơn giản hóa sự phức tạp trong quản lý hệ thống: Hệ thống quản lý có nhiệm vụ chuyển các thông tin hệ thống thành dạng con người có thể hiểu được.
•	Đảm bảo các dịch vụ tin cậy: Quản lý mạng phát hiện lỗi và các mối đe dọa kịp thời đảm bảo trạng thái ổn định và giảm thiểu thời gian ngừng hoạt động của hệ thống.
Kiến trúc hệ thống quản lý mạng:
Theo Internet RFCs thành phần hệ thống mạng phân tán điển hình bao gồm
1.	Network elements: Các thiết bị mạng như: computer, router, server, switch,...
2.	Manager: Người quản lý đưa ra các lệnh và nhận thông báo từ các agent. Thường chỉ có vài manager trên một hệ thống
3.	Agent: Nhận yêu cầu từ manager thực hiện thu thập và lưu trữ các thông tin quản lý được từ các phần tử mạng sau đó gửi lại cho manager. Một agent có hiểu biết về các thông tin quản lý và chuyển đổi chúng sang form tương thích với giao thức quản lý mạng.
4.	Đối tượng quản lý: tài nguyên vật lý: cpu, bộ nhớ, ổ đĩa,…, tài nguyên logic: tốc độ mạng, gói tin dữ liệu, thông lượng, chất lượng đường truyền, Các event log, báo cáo cảnh báo,… dịch vụ mạng: SMTP, …
5.	Network Management Stations: Trạm quản lý mạng hay còn gọi là Trạm điều khiển thực thi các ứng dụng quản lý giám sát và điều khiển các phần tử mạng. Về mặt vật lý, các NMS thường là các máy tính trạm làm việc kỹ thuật có CPU nhanh, màn hình màu mega pixel, bộ nhớ lớn và không gian đĩa dồi dào.
6.	Giao thức quản lý mạng: Một giao thức quản lý được sử dụng để truyền tải thông tin quản lý giữa các đại lý và các trạm quản lý mạng (NMS). Giao thức thông tin quản lý chung (CMIP), Giao thức quản lý mạng đơn giản (SNMP) là giao thức quản lý tiêu chuẩn trên thực tế của cộng đồng Internet.
(Giao thức thông tin quản lý chung (CMIP) là một giao thức quản lý mạng dựa trên OSI. Nó cung cấp triển khai cho các dịch vụ được xác định bởi CMIS (Dịch vụ Thông tin Quản lý Chung), cho phép giao tiếp giữa các ứng dụng quản lý mạng và các agent quản lý.)
7.	Structure of Management Information (SMI): được sử dụng để xác định các quy tắc đặt tên cho các đối tượng và mã hóa các đối tượng trong một trung tâm mạng được quản lý. Nói cách khác, SMI là một ngôn ngữ để xác định một phiên bản cụ thể của dữ liệu trong một trung tâm mạng được quản lý.
SMI chia thành ba phần: định nghĩa mô-đun, định nghĩa đối tượng và định nghĩa thông báo.
8.	Management Information Base (MIB) là một loại cơ sở dữ liệu được sử dụng để quản lý các thiết bị trong mạng truyền thông.

 
The Typical Network Management Architecture
Tương tác giữa NMS và các thiết bị được quản lý có thể là bất kỳ loại lệnh nào trong bốn loại lệnh khác nhau: đọc, ghi, duyệt và bẫy.
• Đọc: Để giám sát các thiết bị được quản lý, NMSs đọc các biến do thiết bị duy trì.
• Ghi: Để điều khiển các thiết bị được quản lý, NMS ghi các biến được lưu trữ trong các thiết bị được quản lý.
• Traverse: NMS sử dụng các hoạt động này để xác định các biến mà thiết bị được quản lý hỗ trợ và để thu thập tuần tự thông tin từ các bảng biến (chẳng hạn như bảng định tuyến IP) trong các thiết bị được quản lý.
• Bẫy: Các thiết bị được quản lý sử dụng bẫy để báo cáo không đồng bộ các sự kiện nhất định cho NMS.
SNMP
SNMP cho phép quản trị viên mạng quản lý hiệu suất mạng, tìm và giải quyết các sự cố mạng cũng như lập kế hoạch phát triển mạng. SNMP là một công cụ quản lý mạng cho phép người quản trị mạng thực hiện các nhiệm vụ giám sát, điều khiển và lập kế hoạch trên mạng được quản lý.
SNMP dựa trên giao thức phản hồi yêu cầu không đồng bộ được cải tiến với tính năng thăm dò theo hướng bẫy. Không đồng bộ định tính đề cập đến thực tế là giao thức không cần đợi phản hồi trước khi gửi các thông báo khác. Thăm dò có điều hướng đề cập đến việc người quản lý thăm dò ý kiến để phản hồi thông báo bẫy được gửi bởi một tác nhân, xảy ra khi có một ngoại lệ hoặc sau khi một số biện pháp đã đạt đến một giá trị ngưỡng nhất định. SNMP hoạt động theo cách không kết nối với UDP là phương thức truyền tải ưu tiên.
Trình quản lý SNMP gửi thông báo đến một tác nhân qua cổng đích UDP 161, trong khi tác nhân gửi thông báo bẫy tới trình quản lý thông qua cổng đích UDP 162. Chế độ không kết nối được chọn một phần để đơn giản hóa việc triển khai SNMP và vì không kết nối thường là chế độ ưu tiên cho các ứng dụng quản lý mà cần phải nói chuyện với nhiều đại lý.
 
SNMP Protocol
Thiết kế mô-đun của SNMP được thể hiện ở sự nhất quán về kiến trúc, cấu trúc và khuôn khổ của cả ba phiên bản; điều này hỗ trợ sự phát triển dần dần của các cải tiến giao thức. Mặc dù SNMPv1 rất hiệu quả và dễ thực hiện, nó cũng có những vấn đề và hạn chế. Các cải tiến cho SNMPv1, dẫn đến một phiên bản SNMP mới, SNMPv2, cũng đã sửa các lỗi và hạn chế trong SNMPv1. Tuy nhiên, những cải tiến mới này không giải quyết được các thiếu sót về bảo mật, chẳng hạn như quyền riêng tư của dữ liệu, giả mạo và tiết lộ trái phép dữ liệu. Sau đó, SNMPv3 sau đó được phát triển để giải quyết những thiếu sót về bảo mật này: SNMPv3 bổ sung các tính năng bảo mật, chẳng hạn như kiểm soát truy cập, xác thực và mã hóa dữ liệu quản lý. Các thông số kỹ thuật SNMPv3 đã được Nhóm Chỉ đạo Kỹ thuật Internet (IESG) phê duyệt là Tiêu chuẩn Internet đầy đủ vào tháng 3 năm 2002 và các nhà cung cấp đã bắt đầu hỗ trợ SNMPv3 trong các sản phẩm của họ.
SNMPv1:
SNMPv1 là Khung quản lý mạng chuẩn Internet ban đầu, như được mô tả trong RFCs 1155, 1157 và 1212. Thường có ba cộng đồng trong SNMPv1: chỉ đọc, đọc-ghi và bẫy. Cần lưu ý rằng mặc dù SNMPv1 là lịch sử nhưng nó vẫn là cách triển khai SNMP chính mà nhiều nhà cung cấp hỗ trợ.
Bảo mật của SNMPv1 dựa trên các cộng đồng, không có gì khác ngoài mật khẩu: các chuỗi văn bản thuần túy cho phép bất kỳ ứng dụng dựa trên SNMP nào biết các chuỗi đó để có quyền truy cập vào thông tin quản lý của thiết bị.
SNMPv1 là một giao thức yêu cầu / phản hồi đơn giản. Hệ thống quản lý mạng đưa ra yêu cầu và các thiết bị được quản lý trả lại phản hồi. Hành vi này được thực hiện bằng cách sử dụng một trong bốn hoạt động giao thức: Get, GetNext, Set và Trap.
SNMPv2


1. Network elements: Các thiết bị mạng như: computer, router, server, switch,...
2. Manager: Người quản lý đưa ra các lệnh và nhận thông báo từ các agent. Thường chỉ có vài manager trên một hệ thống
3. Agent: Nhận yêu cầu từ manager thực hiện thu thập và lưu trữ các thông tin quản lý được từ các phần tử mạng sau đó gửi lại cho manager. Một agent có hiểu biết về các thông tin quản lý và chuyển đổi chúng sang form tương thích với giao thức quản lý mạng.
4. Đối tượng quản lý: tài nguyên vật lý và logic: cpu, dung lượng, nhiệt độ.
