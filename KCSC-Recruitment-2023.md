---
title: Markdown quick start guide

---

                                                                                           Nguyễn_Hoàng_Dương_AT180513_MB
Đầu tiên đến với bài VBS của FOR:
                                                               ![image](https://hackmd.io/_uploads/BklrGLEGee.png)
                    
Tải chall về thì thấy có 1 tệp zip bị khóa bởi mật khẩu và trong đấy là tệp VBS giống tên đề bài : 

 ![image](https://hackmd.io/_uploads/H1wDMINzgg.png)
                   
Đề không cho pass để giải nén nên mình nghĩ ngay đến zip2john để crack mật khẩu:
 ![image](https://hackmd.io/_uploads/r1muM8NMgg.png)
                                                                           
Vậy mật khẩu đã được crack là kma9239 lấy nó để giải nén thôi.Sau khi giải nén mở tệp VBS được như hình: 
 ![image](https://hackmd.io/_uploads/H16HVINGxg.png)

                                                             
Lấy url trong file đưa lên trình duyệt để xem có gì :
                           ![image](https://hackmd.io/_uploads/H1o84LEMge.png)

Không tìm thấy gì ở đường link này cả sau khi suy nghĩ 1 lúc thì mình nhận ra có 1 đường link nhỏ khác trong đường link này:
                         ![image](https://hackmd.io/_uploads/rkOvNL4Gge.png)
             
Thấy ngay mã base64 sau khi giải mã là ra flag:
 ![image](https://hackmd.io/_uploads/SJ4ONI4zge.png)

Flag: KCSC{Vb4_h01_lor""_ae_th0ng_c4m_=(((}
                                                           ![image](https://hackmd.io/_uploads/HkYKVI4fgl.png)
Đây là bài tiếp theo mà mình làm được.Tải về thấy rất nhiều log evtx nhìn rất rối mắt
      ![image](https://hackmd.io/_uploads/SkgVLLEzgg.png)
                                                         
Và câu hỏi đầu tiên của bài là :
   ![image](https://hackmd.io/_uploads/ry7_PLNMee.png)
                                                                       
Sau khi lướt qua các log thấy toàn xuất hiện mỗi 1 máy là FanAnhB mình gửi trả lời xem và thấy chính xác
                         ![image](https://hackmd.io/_uploads/ByxRvL4Mee.png)
                   
                                                
Mình mở file Windows Powershell.evtx lên kiểm tra thì thấy 1 đoạn shell code đáng ngờ của kẻ tấn công 
    ![image](https://hackmd.io/_uploads/ryRhQt4fgg.png)

                                           
Đoạn shell code này có vẻ như là 1 công cụ tương tác từ xa do kẻ tấn công điều khiển thông qua kết nối TCP,nhìn userId là ethan nên mình nộp và kết quả đúng
             ![image](https://hackmd.io/_uploads/S1g2p7KEzeg.png)
![image](https://hackmd.io/_uploads/HJc0mK4Mle.png)
                                                 
                                                             
Nhìn vào đoạn mã trên có vẻ như kẻ tấn công đang tải 1 tệp khả nghi từ địa chỉ 192.168.11.129 
 ![image](https://hackmd.io/_uploads/HJDJEFVfxx.png)

Sau khi tìm thông tin ở tệp Windows Powershell.evtx không có kết quả mình thấy có 1 tệp powershell khác có kích thước lớn hơn so với các tệp còn lại nên mình mở ra xem
 ![image](https://hackmd.io/_uploads/HyKxVtVGxe.png)
![image](https://hackmd.io/_uploads/SyrZ4YEfex.png)

 
Mình thấy rằng đây là đoạn mã sao chép tệp tin "sadboy.bat" từ thư mục Temp đến thư mục StartUp để đảm bảo rằng tệp tin sẽ được thực hiện khi hệ thống khởi động
                                                       
 ![image](https://hackmd.io/_uploads/SkWzVFEfxx.png)
![image](https://hackmd.io/_uploads/H1GVNF4flg.png)

Câu 5 khá dễ sai chỉ cần thừa khoảng trắng là sai :v
![image](https://hackmd.io/_uploads/HyoVNtNMel.png)
![image](https://hackmd.io/_uploads/ByvB4K4Gle.png)

 
Sau khi tìm kiếm khá lâu thì mình thấy file ./p.exe đang cố để tự động chấp nhận các điều khoản giấy phép (End User License Agreement - EULA) mà chương trình có thể yêu cầu lấy từ file lsass.dmp và lướt thêm vài log thấy file ấy bị sử dụng khá nhiều
![image](https://hackmd.io/_uploads/BJ0BVKNzle.png)

![image](https://hackmd.io/_uploads/ryuLNKEfgl.png)
                                 
 
có vẻ như kẻ tấn công đang truy vấn thông tin về tài khoản người dùng trên một miền sử dụng lệnh net user /domain, Danh sách các tài khoản người dùng trên miền, bao gồm "Administrator," "chris," "ethan,".Có vẻ kẻ tấn công đang muốn nhắm đến Administrator
Đó là câu hỏi cuối cùng của bài và mình đã nhận được flag:
        ![image](https://hackmd.io/_uploads/HJMvNFVMeg.png)
                                                
Flag: KCSC{521f1068aee21539b0cb5ea74883018b}
Tham khảo thêm: https://hackmd.io/@codingmagic/rywCzHTIT






                                                      



