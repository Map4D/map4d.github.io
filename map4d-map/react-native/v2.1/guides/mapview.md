# Map4D Map React Component

> Map4dMap React Native cung cấp `MFMapView` dưới dạng một React Component để hiển thị Map4d.


## MFMapView Component

### React view props

| No. | Name                    | Type                        | Description                                                                                                                   |
|:---:|-------------------------|-----------------------------|-------------------------------------------------------------------------------------------------------------------------------|
|  1  | camera                  | [CameraShape](#CameraShape) | Vị trí của camera trên bản đồ.                                                                                                |
|  2  | mapType                 | string                      | Kiểu tiles hiển thị của bản đồ, `roadmap` hoặc `raster`                                                                       |
|  3  | showsMyLocationButton   | bool                        | Ẩn hoặc hiển thị nút vị trí của tôi                                                                                           |
|  4  | showsMyLocation         | bool                        | Ẩn hoặc hiển thị vị trí của tôi.<br>Bật tính năng này yêu cầu thêm quyền vị trí đối với cả Android và iOS.                    |
|  5  | showsBuildings          | bool                        | Ẩn hoặc hiển thị các đối tượng 3D của Map4D (ở chế độ 3D).                                                                    |
|  6  | showsPOIs               | bool                        | Ẩn hoặc hiển thị các địa điểm của Map4D (ở chế độ 2D).                                                                        |
|  7  | onMapReady              | func                        | Được gọi khi bản đồ sẵn sàng để sử dụng.                                                                                      |
|  8  | [onPress](#OnPressData) | func                        | Được gọi khi người dùng tap trên bản đồ (không phải tap vào địa điểm, building hay annotations).                              |
|  9  | [onPoiPress](#OnPoiPressData) | func                  | Được gọi khi người dùng tap vào địa điểm trên bản đồ (không phải POI annotation)                                              |
|  10 | [onBuildingPress](#OnBuildingPressData) | func        | Được gọi khi người dùng tap vào đối tượng 3D trên bản đồ (không phải building annotation)                                     |
|  11 | [onPlacePress](#OnPlacePressData) | func              | Được gọi khi người dùng tap vào place text trên bản đồ (đối với mapType là roadmap)                                           |
|  12 | [onModeChange](#OnModeChangeData) | func              | Được gọi khi bản đồ chuyển từ 2D sang 3D và ngược lại.                                                                        |
|  13 | [onCameraMove](#OnCameraMoveData) | func              | Được gọi liên tục khi camera di chuyển.                                                                                       |
|  14 | [onCameraMoveStart](#OnCameraMoveStartData) | func    | Được gọi khi camera bắt đầu di chuyển.                                                                                        |
|  15 | [onCameraIdle](#OnCameraIdleData) | func              | Được gọi khi camera di chuyển kết thúc,<br>không có hoạt động nào đang chờ xử lý và người dùng đã ngừng tương tác với bản đồ. |
|  16 | [onMyLocationButtonPress](#OnMyLocationButtonPressData)| func | Được gọi khi người dùng chạm vào nút vị trí của tôi                                                                   |
|  17 | [onShouldChangeMapMode](#OnShouldChangeMapModeData)| func | Được gọi khi mức zoom của bản đồ thay đổi từ 16-> 17 và ngược lại (mức chỉ có thể hiển thị 2D và mức có thể hiển thị 3D)  |

### Methods

| No. | Name               | Return Type                       | Arguments                            | Description                                                             |
|:---:|--------------------|-----------------------------------|--------------------------------------|-------------------------------------------------------------------------|
|  1  | getCamera          | [CameraShape](#CameraShape)       |                                      | Lấy giá trị mức zoom hiện tại của bản đồ.                               |
|  2  | moveCamera         |                                   | [CameraShape](#CameraShape) `camera` | Di chuyển camera đến vị trí `camera` ngay lập tức.                      |
|  3  | animateCamera      |                                   | [CameraShape](#CameraShape) `camera` | Di chuyển camera đến vị trí `camera` với hiệu ứng di chuyển.            |
|  4  | cameraForBounds    | [CameraShape](#CameraShape)       | [BoundsData](#BoundsData) `bounds`   | Lấy giá trị camera đối với `bounds`                                     |
|  5  | fitBounds          |                                   | [BoundsData](#BoundsData) `bounds`   | Di chuyển camera đến ví trí thích hợp với `bounds`                      |
|  6  | getBounds          | [BoundsData](#BoundsData)         |                                      | Lấy vùng hiển thị hiện tại của bản đồ.                                  |
|  7  | is3DMode           | bool                              |                                      | Kiểm tra mode hiện tại của bản đồ có phải là 3D hay không               |
|  8  | enable3DMode       |                                   | bool `enable`                        | Set chế độ 2D, 3D cho bản đồ, `true` thì sẽ hiển thị bản đồ ở chế độ 3D |
|  9  | setTime            |                                   | string                               | Set time cho bản đồ                                                     |
|  10 | coordinateForPoint | [CoordinateData](#CoordinateData) | [PointData](#PointData)              | Convert tọa độ màn hình x,y sang tọa độ kinh độ, vĩ độ                  |
|  11 | pointForCoordinate | [PointData](#PointData)           | [CoordinateData](#CoordinateData)    | Convert tọa độ kinh độ, vĩ độ sang tọa độ màn hình x,y                  |

### Object Types

#### PointData

Thông tin tọa độ 2 chiều x, y

```js
let point = {x: 1, y: 2}
```

#### CoordinateData

Thông tin tọa độ theo kinh độ, vĩ độ

```js
let coordinate = {latitude: 10.7881732, longitude: 106.7000933}
```

#### CameraShape

CameraShape là một kiểu dữ liệu lưu các thông tin của camera. Có cấu trúc như sau:

```js
{
  center: {
    latitude: number,
    longitude: number,
  },
  zoom: number,
  bearing: number,
  tilt: number
}
```

Ví dụ sử dụng:

```js
var camera = {
  center: {
    latitude: 10.7881732,
    longitude: 106.7000933
  },
  zoom: 16,
  bearing: 0,
  tilt: 0,
}
```

#### BoundsData

Bounds Data là một object chứa thông tin latitude, longitude của một khu vực và padding

Ví dụ sử dụng:
```js
let boundsData = {
  bounds: {
    northEast: { latitude: 16.07102188912311, longitude: 108.22186589241028 },
    southWest: { latitude: 16.07302188912311, longitude: 108.25186589241028 }
  },
  padding: { top: 1, right: 2, bottom: 3, left: 4 }
}
```

#### OnPressData

On Press Data là một object chứa thông tin trả về của sự kiện onPress.

Ví dụ:
```js
{
  "action": "map-press",
  "location": {
    "latitude": 10.786622402809513,
    "longitude": 106.69969404367612
  },
  "pixel": {
    "x": 357.967529296875,
    "y": 1233.9140625
  }
}
```

Các thông tin của dữ liệu trả về như sau:
- **location** : tọa độ trên bản đồ mà người dùng press.
- **pixel** : tọa độ trên màn hình mà người dùng press.

#### OnPoiPressData

On Poi Press Data là một object chứa thông tin trả về của sự kiện onPoiPress.

Ví dụ:
```js
{
  "action": "map-poi-press",
  "location": {
    "latitude": 10.788482797843585,
    "longitude": 106.69818604091677
  },
  "pixel": {
    "x": 193.963623046875,
    "y": 744.94921875
  },
  "poi": {
    "location": {
      "latitude": 10.788311,
      "longitude": 106.698198
    },
    "id": "5c9845e4814a9df9d67e5aaa",
    "title": "Trường THCS Trần Văn Ơn"
  }
}
```

Các thông tin của dữ liệu trả về như sau:
- **location** : tọa độ trên bản đồ mà người dùng press.
- **pixel** : tọa độ trên màn hình mà người dùng press.
- **poi** : dữ liệu của POI gồm `location`, `id` và `title`.

#### OnBuildingPressData

On Building Press Data là một object chứa thông tin trả về của sự kiện onBuildingPress.

Ví dụ:
```js
{
  "action": "map-building-press",
  "building": {
    "id": "5fab913686a8b557d9138d3c",
    "location": {
      "latitude": 10.78648718805124,
      "longitude": 106.70222441989614
    },
    "name": "Đài Truyền hình Thành phố Hồ Chí Minh"
  },
  "location": {
    "latitude": 10.786818627961509,
    "longitude": 106.7024116463657
  },
  "pixel": {
    "x": 545.965576171875,
    "y": 887.91796875
  }
}
```

Các thông tin của dữ liệu trả về như sau:
- **location** : tọa độ trên bản đồ mà người dùng press.
- **pixel** : tọa độ trên màn hình mà người dùng press.
- **poi** : dữ liệu của Building gồm `location`, `id` và `name`.

#### OnPlacePressData

On Place Press Data là một object chứa thông tin trả về của sự kiện onPlacePress.

Ví dụ:
```js
{
  "action": "map-place-press",
  "location": {
    "latitude": 10.7799990958611,
    "longitude": 106.7021948112598
  },
  "pixel": {
    "x": 560.9619140625,
    "y": 1093.93359375
  },
  "place": {
    "location": {
      "latitude": 10.780834541593762,
      "longitude": 106.70282363891602
    },
    "name": "P. Bến Nghé"
  }
}
```

Các thông tin của dữ liệu trả về như sau:
- **location** : tọa độ trên bản đồ mà người dùng press.
- **pixel** : tọa độ trên màn hình mà người dùng press.
- **place** : dữ liệu của Place gồm `location` và `name`.

#### OnModeChangeData

On Mode Change Data là một object chứa thông tin trả về của sự kiện onModeChange.

Ví dụ:
```js
{
  "action": "mode-change",
  "mode": "3d"
}
```

Các thông tin của dữ liệu trả về như sau:
- **mode** : mode hiện tại của Map.

#### OnCameraMoveData

On Camera Move Data là một object chứa thông tin trả về của sự kiện onCameraMove.

Ví dụ:
```js
{
  "action": "camera-move",
  "bearing": 0,
  "center": {
    "latitude": 10.790166360485987,
    "longitude": 106.69945700663592
  },
  "tilt": 0,
  "zoom": 17
}
```

Các thông tin của dữ liệu trả về như sau:
- **center** : tạo độ hiện tại của camera.
- **bearing** : góc quay hiện tại của camera ((đơn vị là Độ)).
- **tilt** : góc nghiêng hiện tại của camera (đơn vị là Độ).
- **zoom** : mức zoom hiện tại của camera.

#### OnCameraMoveStartData

On Camera Move Start Data là một object chứa thông tin trả về của sự kiện onCameraMoveStart.

Ví dụ:
```js
{
  "action": "camera-move-started",
  "bearing": 0,
  "center": {
    "latitude": 10.790166360485987,
    "longitude": 106.69945700663592
  },
  "gesture": true,
  "tilt": 0,
  "zoom": 17
}
```

Các thông tin của dữ liệu trả về như sau:
- **center** : tạo độ hiện tại của camera.
- **bearing** : góc quay hiện tại của camera ((đơn vị là Độ)).
- **tilt** : góc nghiêng hiện tại của camera (đơn vị là Độ).
- **zoom** : mức zoom hiện tại của camera.
- **gesture** : camera di chuyển có phải do tác động của người dùng hay không.

#### OnCameraIdleData

On Camera Idle Data là một object chứa thông tin trả về của sự kiện onCameraIdle.

Ví dụ:
```js
{
  "action": "camera-idle",
  "bearing": 0,
  "center": {
    "latitude": 10.790403491127114,
    "longitude": 106.70022538767377
  },
  "tilt": 0,
  "zoom": 17
}
```

Các thông tin của dữ liệu trả về như sau:
- **center** : tạo độ hiện tại của camera.
- **bearing** : góc quay hiện tại của camera ((đơn vị là Độ)).
- **tilt** : góc nghiêng hiện tại của camera (đơn vị là Độ).
- **zoom** : mức zoom hiện tại của camera.

#### OnMyLocationButtonPressData

On My Location Button Press Data là một object chứa thông tin trả về của sự kiện onMyLocationButtonPress.

Ví dụ:
```js
{
  "action": "my-location-button-press"
}
```

#### OnShouldChangeMapModeData

On Should Change Map Mode Data là một object chứa thông tin trả về của sự kiện onShouldChangeMapMode.

Ví dụ:
```js
{
  "action": "should-change-mode"
}
```
