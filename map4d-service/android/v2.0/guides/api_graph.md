# Graph Route

> Tìm biểu đồ tuyến đường giữa các địa điểm.

## Usage

Để sử dụng service Graph Route ta sử dụng phương thức sau đây của class [MFDirectionsService](reference/directions-service?id=mfplacesservice)

**Methods**

| Name              | Parameters                              | Return Value | Description                                                                            |
|-------------------|:---------------------------------------:|:------------:|----------------------------------------------------------------------------------------|
|**fetchGraphRoute**| [MFGraphRouteOptions](/guides/api_graph?id=mfgraphrouteoptions), [MFServiceCallback](types?id=mfservicecallback)<[MFGraphRoute](/guides/api_graph?id=mfgraphroute)[]>|[MFServiceTask](types?id=mfservicetask)| Gọi API Graph Route với kết quả trả về là mảng **MFGraphRoute** |

Ví dụ:

<!-- tabs:start -->
#### ** Kotlin **
```kotlin
val points = listOf(
  MFLocationComponent(16.039173, 108.210912),
  MFLocationComponent(16.0825981, 108.2219887)
)

val mfGraphRouteOptions = MFGraphRouteOptions.Builder()
  .points(points)
  .language("vi")
  .weighting(MFRoute.Weighting.FASTEST)
  .restriction(
    MFRouteRestriction.restrictCircleArea(
      MFLocationComponent(16.044597, 108.217263),
      30,
      listOf(MFRouteRestriction.MFRouteType.MOTORWAY, MFRouteRestriction.MFRouteType.BRIDGE))
  )
  .build()
  
val serviceOption = MFServicesOptions.Builder(this).build()
val directionServices = MFDirectionsService(serviceOption)
directionServices.fetchGraphRoute(mfGraphRouteOptions, object : MFServiceCallback<Array<MFGraphRoute>> {
  override fun onSuccess(data: Array<MFGraphRoute>?) {
    data?.let {
      Log.e("Graph Route", "Graph Routes:  ${it?.contentToString()}")
    }
  }

  override fun onError(code: String?, message: String?) {
    Log.e("Graph Route", "Error:  $code , message: $message")
  }
})
```
#### ** Java **
```java
List<MFLocationComponent> points = Arrays.asList(
  new MFLocationComponent(16.039173, 108.210912),
  new MFLocationComponent(16.0825981, 108.2219887)
);

MFGraphRouteOptions mfGraphRouteOptions = new MFGraphRouteOptions.Builder()
  .points(points)
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
directionServices.fetchGraphRoute(mfGraphRouteOptions, new MFServiceCallback<MFGraphRoute[]>() {
  @Override
  public void onSuccess(@Nullable MFGraphRoute[] data) {
    // Do something
  }

  @Override
  public void onError(String code, String message) {
    Log.e("Graph Route Error", "Error message: " + message);
  }
});
```
<!-- tabs:end -->

## MFGraphRouteOptions

Đối tượng `MFGraphRouteOptions` dùng để xác định các thuộc tính dùng cho [MFDirectionsService](reference/directions-service?id=mfplacesservice)

Để tạo đối tượng `MFGraphRouteOptions` thì ta tạo thông qua class [MFGraphRouteOptions.Builder](/guides/api_graph?id=mfgraphrouteoptionsbuilder)

<!-- tabs:start -->
#### ** Kotlin **
```kotlin
val points = listOf(
  MFLocationComponent(16.039173, 108.210912),
  MFLocationComponent(16.0825981, 108.2219887)
)

val mfGraphRouteOptions = MFGraphRouteOptions.Builder()
  .points(points)
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
List<MFLocationComponent> points = Arrays.asList(
  new MFLocationComponent(16.039173, 108.210912),
  new MFLocationComponent(16.0825981, 108.2219887)
);

MFGraphRouteOptions mfGraphRouteOptions = new MFGraphRouteOptions.Builder()
  .points(points)
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
| **getPoints**                | `none` | List<[MFLocationComponent](/types?id=mflocationcomponent)> | Lấy danh sách các địa điểm                                    |
| **getMode**                  | `none` |[MFTravelMode](/types?id=mftravelmode)| Lấy mode (loại phương tiện) di chuyển               |
| **getLanguage**              | `none`          | String       | Lấy ngôn ngữ chỉ đường của options                                 |
| **getWeighting**             | `none` |[MFWeighting](/types?id=mfweighting)| Lấy giá trị thuộc tính đường đi            |
| **getRestriction**           | `none` |[MFRouteRestriction](/types?id=mfrouterestriction)| Lấy điểm / khu vực / danh sách các loại đường mà tuyến đường không đi qua    |
| **getAvoidRoads**            | `none` |List<[MFRouteRestriction.MFRouteType](/types?id=mfrouterestrictionmfroutetype)>| Lấy danh sách các loại đường cấm đi qua         |

## MFGraphRouteOptions.Builder

**Constructor**

Tạo đối tượng `MFGraphRouteOptions.Builder`

```
MFGraphRouteOptions.Builder()
```

**Methods**

| Name                    | Parameters      | Return Value | Description                                                        |
|-------------------------|:---------------:|:------------:|--------------------------------------------------------------------|
| **points** *required*     | List<[MFLocationComponent](/types?id=mflocationcomponent)> | Builder      | Set danh sách các địa điểm cho Builder                |
| **mode** *optional* |[MFTravelMode](/types?id=mftravelmode)| Builder | Set loại phương tiện cho Builder. Mặc định là MFTravelMode.CAR |
| **language** *optional* | String | Builder | Set ngôn ngữ chỉ đường cho Builder                                               |
| **weighting** *optional* |[MFWeighting](/types?id=mfweighting)| Builder | Set thuộc tính đường đi cho Builder      |
| **restriction** *optional*  |[MFRouteRestriction](/types?id=mfrouterestriction)| Builder      | Set điểm / khu vực / danh sách các loại đường mà tuyến đường không đi qua cho Builder|
| **build**               | `none`          |[MFGraphRouteOptions](/guides/api_graph?id=mfgraphrouteoptions)| Tạo đối tượng MFGraphRouteOptions từ Builder|

## MFGraphRoute

> Là đối tượng được trả về từ callback khi gọi API Distance Matrix.

**Methods**

| Name                         | Parameters      | Return Value | Description                                                        |
|------------------------------|:---------------:|:------------:|--------------------------------------------------------------------|
| **getId**                    | `none` | String | Lấy id của graph route                                                           |
| **getDistance**              | `none` |[MFGraphRoute.Info](/guides/api_graph?id=mfgraphrouteinfo)  | Lấy thông tin khoảng các của graph route                           |
| **getDuration**              | `none` |[MFGraphRoute.Info](/guides/api_graph?id=mfgraphrouteinfo)| Lấy thông tin khoảng thòi gian của graph route |
| **getPolyline**              | `none` | String | Lấy thông tin Polyline của route được mã hóa dưới dạng chuỗi String               |
| **getStatus**                | `none` | String | Lấy thông tin trạng thái của graph route       |

## MFGraphRoute.Info

> Thông tin chi tiết của MFGraphRoute

**Methods**

| Name                         | Parameters      | Return Value | Description                                                        |
|------------------------------|:---------------:|:------------:|--------------------------------------------------------------------|
| **getText**                  | `none`          | String       | Lấy thông tin dưới dạng text                                       |
| **getValue**                 | `none`          | Double       | Lấy thông tin dưới dạng số double                                  |
