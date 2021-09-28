# Map Type

## Giới thiệu

>Map4dMap Android SDK cho phép tùy chỉnh kiểu hiển thị của Tile bản đồ theo hai chế độ (Raster Tile và Vector Tile).

* Raster Tile: hiển thị tile bản đồ bằng dữ liệu hình ảnh.
* Vector Tile: hiển thị tile bản đồ bằng dữ liệu gốc, điều này làm cho bản đồ được hiển thị rõ ràng và sắc nét hơn.

### Các loại bản đồ

Map4D Map SDK hiện cung cấp 2 loại bản đồ tùy chỉnh thông qua đối tượng `MFMapType` như bên dưới:

| No. | Name    | Description                                                                                                                                                           |
|:---:|---------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  1  | ROADMAP | Giá trị: `MFMapType.ROADMAP`<br>Các thành phần của bản đồ được vẽ dưới dạng các đường nét và hình khối, có độ phân giải cao<br>Đây là bản đồ mặc định của Map4dMap SDK |
|  2  | RASTER  | Giá trị: `MFMapType.RASTER`<br>Các tiles của bản đồ được hiển thị dưới dạng hình ảnh đã được dựng sẵn, tốc độ tải và hiển thị nhanh hơn so với roadmap.                |

|                 ROADMAP                         | RASTER                                         |
|:-----------------------------------------------:|:----------------------------------------------:|
| ![MapType](../../resources/maptype-roadmap.png) | ![MapType](../../resources/maptype-raster.png) |

### Thay đổi kiểu bản đồ

Để thay kiểu bản đồ, ta set giá trị  một gọi hàm `setMapType(MFMapType mapType)` thông qua đối tượng `Map4D`  
Ví dụ: để hiển thị bản đồ dạng raster:

<!-- tabs:start -->
#### ** Java **

```java
private Map4D map4D;

map4D.setMapType(MFMapType.RASTER);
```

#### ** Kotlin **

```kotlin
private lateinit var map4D: Map4D

map4D.setMapType(MFMapType.RASTER)
```
<!-- tabs:end -->

### Get kiểu bản đồ hiện tại

Để get kiểu bản đồ hiện tại ta có thể gọi hàm `getMapType()` thông qua đối tượng `Map4D`. Giá trị trả về sẽ là một kiểu
của `MFMapType`

Ví dụ:

<!-- tabs:start -->
#### ** Java **

```java
private Map4D map4D;

MFMapType mapType = map4D.getMapType();
```

#### ** Kotlin **

```kotlin
private lateinit var map4D: Map4D

val mapType = map4D.getMapType()
```
<!-- tabs:end -->

