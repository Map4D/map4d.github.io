# Graph Route Params

`MFGraphRouteParams` class

### Public Member Functions

#### initWithLocations:

```objc
- (instancetype)initWithLocations:(NSArray<MFLocationComponent *> *)locations;
```

Tạo đối tượng `MFGraphRouteParams` với các địa điểm locations.

#### initWithLocations: mode: weighting:

```objc
- (instancetype)initWithLocations:(NSArray<MFLocationComponent *> *)locations mode:(MFTravelMode)mode weighting:(MFRouteWeighting)weighting;
```

Tạo đối tượng `MFGraphRouteParams` với các tham số locations, mode và weighting.

### Properties

| Name        | Type                                                            | Description                                                                        |
|-------------|-----------------------------------------------------------------|------------------------------------------------------------------------------------|
| locations   | NSArray<[MFLocationComponent](reference/location-component.md)> | Các địa điểm để thực hiện tính toán biểu đồ.                                       |
| mode        | [MFTravelMode](reference/travel-mode.md)                        | Phương thức di chuyển.                                                             |
| weighting   | [MFRouteWeighting](reference/route-weighting.md)                | Thuộc tính tìm kiếm (đường ngắn nhất, nhanh nhất hay cân bằng).                    |
| restriction | [MFRouteRestriction](reference/route-restriction.md)            | Điểm, khu vực, loại đường bị loại bỏ mà tuyến đường được tìm kiếm sẽ không đi qua. |
| language    | [MFLanguageResult](reference/language-result.md)                | Ngôn ngữ dùng để chỉ đường.                                                        |
