# Route ETA

> Tìm thời gian dự kiến của đường đi giữa các địa điểm.

## Usage

Để sử dụng service Route ETA ta sử dụng phương thức sau đây của class [MFDirectionsService](reference/directions-service?id=mfplacesservice)

**Methods**

| Name              | Parameters                              | Return Value | Description                                                                            |
|-------------------|:---------------------------------------:|:------------:|----------------------------------------------------------------------------------------|
| **fetchRouteETA** | [MFRouteEtaOptions](/guides/api_eta?id=mfrouteetaoptions), [MFServiceCallback](types?id=mfservicecallback)<[MFRouteEta](types?id=mfroute)[]>|[MFServiceTask](types?id=mfservicetask)| Gọi API Route ETA với kết quả trả về là mảng **MFRouteEta** |

Ví dụ:

<!-- tabs:start -->
#### ** Kotlin **
```kotlin
val origins = listOf(
  MFLocationComponent(16.039173, 108.210912, "alias1"),
  MFLocationComponent(16.039402, 108.211080, "alias2")
)

val mfRouteEtaOptions = MFRouteEtaOptions.Builder()
  .origins(origins)
  .destination(MFLocationComponent(16.0825981,108.2219887))
  .language("vi")
  .weighting(MFRoute.Weighting.FASTEST)
  .restriction(
    MFRouteRestriction.restrictCircleArea(
      MFLocationComponent(16.044597, 108.217263),
      30,
      listOf(MFRouteRestriction.MFRouteType.MOTORWAY, MFRouteRestriction.MFRouteType.BRIDGE))
  )
  .build()

val options = MFServicesOptions.Builder(this).build()
val directionServices = MFDirectionsService(options)
directionServices.fetchRouteETA(mfRouteEtaOptions, object: MFServiceCallback<Array<MFRouteEta>> {
  override fun onSuccess(data: Array<MFRouteEta>?) {
    data?.let {
      Log.e("Route Eta", "Route Eta:  ${it?.contentToString()}")
    }
  }

  override fun onError(code: String?, message: String?) {
    Log.e("Route Eta", "Error:  $code , message: $message")
  }
})
```
#### ** Java **
```java
List<MFLocationComponent> origins = Arrays.asList(
  new MFLocationComponent(16.039173, 108.210912, "alias1"),
  new MFLocationComponent(16.039402, 108.211080, "alias2")
);

MFRouteEtaOptions mfRouteEtaOptions = new MFRouteEtaOptions.Builder()
  .origins(origins)
  .destination(new MFLocationComponent(16.0825981, 108.2219887))
  .language("vi")
  .weighting(MFWeighting.FASTEST)
  .restriction(
    MFRouteRestriction.restrictCircleArea(
      new MFLocationComponent(16.044597, 108.217263),
      30,
      Arrays.asList(MFRouteRestriction.MFRouteType.MOTORWAY, MFRouteRestriction.MFRouteType.BRIDGE))
  )
  .build();

MFServicesOptions options = new MFServicesOptions.Builder(this).build();
MFDirectionsService directionServices = new MFDirectionsService(options);
directionServices.fetchRouteETA(mfRouteEtaOptions, new MFServiceCallback<MFRouteEta[]>() {
  @Override
  public void onSuccess(@Nullable MFRouteEta[] data) {
    // Do something
  }

  @Override
  public void onError(String code, String message) {
    Log.e("Route ETA Error", "Error message: " + message);
  }
});
```
<!-- tabs:end -->

## MFRouteEtaOptions

Đối tượng `MFRouteEtaOptions` dùng để xác định các thuộc tính dùng cho [MFDirectionsService](reference/directions-service?id=mfplacesservice)

Để tạo đối tượng `MFRouteEtaOptions` thì ta tạo thông qua class [MFRouteEtaOptions.Builder](/guides/api_eta?id=mfrouteetaoptionsbuilder)

<!-- tabs:start -->
#### ** Kotlin **
```kotlin
val origins = listOf(
  MFLocationComponent(16.039173, 108.210912, "alias1"),
  MFLocationComponent(16.039402, 108.211080, "alias2")
)

val mfRouteEtaOptions = MFRouteEtaOptions.Builder()
  .origins(origins)
  .destination(MFLocationComponent(16.0825981,108.2219887))
  .language("vi")
  .weighting(MFRoute.Weighting.FASTEST)
  .restriction(
    MFRouteRestriction.restrictCircleArea(
      MFLocationComponent(16.044597, 108.217263),
      30,
      listOf(MFRouteRestriction.MFRouteType.MOTORWAY, MFRouteRestriction.MFRouteType.BRIDGE))
  )
  .build()
```
#### ** Java **
```java
List<MFLocationComponent> origins = Arrays.asList(
  new MFLocationComponent(16.039173, 108.210912, "alias1"),
  new MFLocationComponent(16.039402, 108.211080, "alias2")
);

MFRouteEtaOptions mfRouteEtaOptions = new MFRouteEtaOptions.Builder()
  .origins(origins)
  .destination(new MFLocationComponent(16.0825981, 108.2219887))
  .language("vi")
  .weighting(MFWeighting.FASTEST)
  .restriction(
    MFRouteRestriction.restrictCircleArea(
      new MFLocationComponent(16.044597, 108.217263),
      30,
      Arrays.asList(MFRouteRestriction.MFRouteType.MOTORWAY, MFRouteRestriction.MFRouteType.BRIDGE))
  )
  .build();
```
<!-- tabs:end -->

**Methods**

| Name                         | Parameters      | Return Value | Description                                                        |
|------------------------------|:---------------:|:------------:|--------------------------------------------------------------------|
| **getOrigins**               | `none` | List<[MFLocationComponent](/types?id=mflocationcomponent)>  | Lấy danh sách vị trí các điểm xuất phát                                  |
| **getDestination**           | `none` | [MFLocationComponent](/types?id=mflocationcomponent) | Lấy vị trí điểm kết thúc                                           |
| **getMode**                  | `none` |[MFTravelMode](/types?id=mftravelmode)| Lấy mode (loại phương tiện) di chuyển               |
| **getLanguage**              | `none`          | String       | Lấy ngôn ngữ chỉ đường                                             |
| **getWeighting**             | `none` |[MFWeighting](/types?id=mfweighting)| Lấy giá trị thuộc tính đường đi            |
| **getRestriction**           | `none` |[MFRouteRestriction](/types?id=mfrouterestriction)| Lấy điểm / khu vực / danh sách các loại đường mà tuyến đường không đi qua    |
| **getAvoidRoads**            | `none` |List<[MFRouteRestriction.MFRouteType](/types?id=mfrouterestrictionmfroutetype)>| Lấy danh sách các loại đường cấm đi qua         |

## MFRouteEtaOptions.Builder

**Constructor**

Tạo đối tượng `MFRouteEtaOptions.Builder`

```
MFRouteEtaOptions.Builder()
```

**Methods**

| Name                    | Parameters      | Return Value | Description                                                        |
|-------------------------|:---------------:|:------------:|--------------------------------------------------------------------|
| **origins** *required*  | List<[MFLocationComponent](/types?id=mflocationcomponent)> | Builder      | Set các vị trí xuất phát cho Builder                     |
| **destination** *required* | [MFLocationComponent](/types?id=mflocationcomponent) | Builder | Set vị trí kết thúc cho Builder                                 |
| **mode** *optional* |[MFTravelMode](/types?id=mftravelmode)| Builder | Set loại phương tiện cho Builder. Mặc định là MFTravelMode.CAR|
| **language** *optional* | String | Builder | Set ngôn ngữ chỉ đường cho Builder                                               |
| **weighting** *optional* |[MFWeighting](/types?id=mfweighting)| Builder | Set thuộc tính đường đi cho Builder      |
| **restriction** *optional*  |[MFRouteRestriction](/types?id=mfrouterestriction)| Builder      | Set điểm / khu vực / danh sách các loại đường mà tuyến đường không đi qua cho Builder|
| **build**               | `none`          |[MFRouteEtaOptions](/guides/api_eta?id=mfrouteetaoptions)| Tạo đối tượng MFRouteEtaOptions từ Builder|

## MFRouteEta

> Đối tượng trả về từ callback khi gọi API Route ETA

**Methods**

| Name                         | Parameters      | Return Value | Description                                                        |
|------------------------------|:---------------:|:------------:|--------------------------------------------------------------------|
| **getAlias**                 | `none` | String  | Lấy thông tin alias                                                              |
| **getLocation**              | `none` | [MFLocationComponent](/types?id=mflocationcomponent) | Lấy thông tin vị trí                                               |
| **getDistance**              | `none` |[MFRouteEta.Info](/guides/api_eta?id=mfrouteetainfo)| Lấy thông tin khoảng cách             |
| **getDuration**              | `none` |[MFRouteEta.Info](/guides/api_eta?id=mfrouteetainfo)| Lấy thông tin khoảng thời gian        |
| **getPolyline**              | `none` | String | Lấy thông tin Polyline của route được mã hóa dưới dạng chuỗi String               |

## MFRouteEta.Info

> Thông tin chi tiết của MFRouteEta

**Methods**

| Name                         | Parameters      | Return Value | Description                                                        |
|------------------------------|:---------------:|:------------:|--------------------------------------------------------------------|
| **getText**                  | `none`          | String       | Lấy thông tin dưới dạng text                                       |
| **getValue**                 | `none`          | Double       | Lấy thông tin dưới dạng số double                                  |
