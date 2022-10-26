# Changelog

## Version 2.4.2

#### Added

- Thêm sự kiện `tiltChanged`, `zoomChanged`, `bearingChanged`, `targetChanged` cho map

## Version 2.4.1

#### Added

- Thêm sự kiện `mouseOut` cho marker

### Changed

- Giảm thời gian time out cho mouse hover và tối ưu query annotations
- Xóa 3D button ở bảng điều khiển mặc định

### Fixed

- Sửa lỗi setAllGesturesEnabled(false) vẫn cho phép zoom map ở chế độ 3D

## Version 2.4.0

Những thay đổi kể từ version 2.3.x

#### Added

- Thêm lớp Image Overlay
- Hỗ trợ opacity cho Tile Overlay, Ground Overlay
- Thêm mới phương thức `fromLatLngToPoint` và `fromPointToLatLng` cho Projection class

### Changed

- Thay đổi phương thức kiểm tra đối tượng

### Fixed

- Sửa lỗi vẽ sai thứ tự POI trong một số trường hợp
- Sửa lỗi crash ở một số trường hợp options chứa giá trị null
- Sửa lỗi màu text hiển thị khi set background cho HTML DOM chưa map view
- Sửa lỗi crash khi gọi map đã bị destroy
- Sửa lỗi khó click vào polyline khi set độ cao ở 3D

<!-- #### Security -->
