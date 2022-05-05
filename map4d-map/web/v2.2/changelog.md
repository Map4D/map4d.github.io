# Changelog

## Version 2.2.0

Những thay đổi kể từ version 2.1.x

#### Added

- Thêm mới `strokePattern` option cho [Polyline](reference/polyline.md)
- Thêm callback `onMarkerDragEnd` khi drag Marker trên [Directions Renderer](reference/directions-renderer.md)

#### Changed

- Update vẽ lớp building ở chế độ Roadmap từ mức zoom 17 trở lên.
- Hỗ trợ mức zoom lẻ (số thực)
- Hỗ trợ thêm các marker waypoint cho [Directions Renderer](reference/directions-renderer.md)

#### Deprecated

- Deprecated option `style` của [Polyline](reference/polyline.md)

#### Removed

#### Fixed

- Fixed lỗi icon của POI bị ẩn khi đè lên nhau.
- Fixed lỗi tên đường bị mất sau khi thực hiện zoom.
- Fixed lỗi khó touch trên Marker tạo với icon là một url.

<!-- #### Security -->
