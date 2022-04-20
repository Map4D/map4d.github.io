#  Load map theo version (Bản đồ 2D trên web)
Get file js theo version.

Cho phép nhà phát triển tích hợp Map4D SDK vào ứng dụng web với đầy đủ tính năng điều khiển. 

Phương thức: **GET**
## 1. Input (Đầu vào)
```
http://api.map4d.vn/sdk/map/js?version={version}&callback={callback}
```
| Parameter | Required | Description                                                                                        |
|---------------|--------------|--------------------------------------------------------------------------------------------------------|
| version       | **Yes**      | Phiên bản nội dung "javascript" Map4D. Chỉ hỗ trợ dạng x.y.z hoặc x.y. Ví dụ: 2.1.0                    |
| callback      | No           | Gọi lại một function sẽ được thực thi sau khi một function khác đã được thực thi xong. Ví dụ: callback |
## 2. Output (Đầu ra)
```text
Trả về nội dung tập tin "javascript " gồm các function liên quan đến bản đồ 2D trên web.
```
[Chức năng nội dung tập tin javascript](https://github.com/map4d/map4d-web-sdk)