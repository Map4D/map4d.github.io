# Changelog

## Version 2.5.2

#### Fixed

- Sửa lỗi không load tiles khi set native zoom quá lớn
- Sửa lỗi không reload tile nếu request bị lỗi
- Sửa lỗi crash khi sử dụng hình ảnh không đúng kích thước
- Sửa lỗi các giá trị `bearing`, `scale`, `elevation` của `MFBuilding` không được áp dụng nếu thiết lập trước khi thêm vào bản đồ

#### Changed

- Cải thiện hiệu suất request, tính toán

## Version 2.5.1

#### Fixed

- Sửa lỗi xoay map theo góc lớn trong một số trường hợp
- Sửa lỗi marker bị nháy khi thay đổi tọa độ liên tục

## Version 2.5.0

Những thay đổi kể từ version 2.4.4

#### Added

- Thêm mới [GeoJSON Layer](guides/geojson.md)

#### Fixed

- Sửa lỗi marker bị nháy khi thay đổi vị trí liên tục
- Sửa lỗi crash khi load đối tượng 3D không đúng định dạng

<!-- #### Changed -->
<!-- #### Deprecated -->
<!-- #### Removed -->
<!-- #### Security -->
