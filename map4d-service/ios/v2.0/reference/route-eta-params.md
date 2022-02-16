# Route ETA Params

`MFRouteETAParams` class

### Public Member Functions

#### initWithOrigins: destination:

```objc
- (instancetype)initWithOrigins:(NSArray<MFLocationComponent *> *)origins destination:(MFLocationComponent *)destination;
```

Tạo đối tượng `MFRouteETAParams` với các điểm bắt đầu *origins* và điểm kết thúc *destination*

#### initWithOrigins: destination: mode: weighting:

```objc
- (instancetype)initWithOrigins:(NSArray<MFLocationComponent *> *)origins
                    destination:(MFLocationComponent *)destination
                           mode:(MFTravelMode)mode
                      weighting:(MFRouteWeighting)weighting;
```

Tạo đối tượng `MFRouteETAParams` với các điểm bắt đầu *origins*, điểm kết thúc *destination*, mode và weighting

### Properties

| Name        | Type                                                            | Description                                                                        |
|-------------|-----------------------------------------------------------------|------------------------------------------------------------------------------------|
| origins     | NSArray<[MFLocationComponent](reference/location-component.md)> | Các điểm bắt đầu dùng để ước lượng thời gian.                                      |
| destination | [MFLocationComponent](reference/location-component.md)          | Vị trí đích.                                                                       |
| mode        | [MFTravelMode](reference/travel-mode.md)                        | Phương thức di chuyển.                                                             |
| weighting   | [MFRouteWeighting](reference/route-weighting.md)                | Thuộc tính tìm kiếm (đường ngắn nhất, nhanh nhất hay cân bằng).                    |
| restriction | [MFRouteRestriction](reference/route-restriction.md)            | Điểm, khu vực, loại đường bị loại bỏ mà tuyến đường được tìm kiếm sẽ không đi qua. |
| language    | [MFLanguageResult](reference/language-result.md)                | Ngôn ngữ dùng để chỉ đường.                                                        |
