# Directions Renderer

Để vẽ chỉ đường giữa các địa điểm trên Map thì ta sử dụng đối tượng `Directions Renderer` thay cho việc vẽ nhiều `Polyline` một cách thủ công.

## 1. DirectionsRenderer & DirectionsRendererOptions
```java
public class MFDirectionsRendererOptions {

  private List<List<MFLocationCoordinate>> paths; // Danh sách tọa độ của các path
  private MFLocationCoordinate startLocation; // Tọa độ của điểm bắt đầu
  private MFLocationCoordinate endLocation; // Tọa độ của điểm kết thúc
  private String jsonData; // Dữ liệu json
  private byte[][] binaryData; // Dữ liệu binary
  private int activedIndex; // chỉ số để xác định path nào đang được active
  @ColorInt
  private int activeStrokeColor; // Màu của line được active
  @ColorInt
  private int activeOutlineColor; // Màu của line không được active
  @ColorInt
  private int inactiveStrokeColor; // Màu viền của line được active
  @ColorInt
  private int inactiveOutlineColor; // Màu viền của line không được active
  @ColorInt
  private int titleColor; // Màu của chữ
  private float width; // Độ rộng của line
  @Nullable
  private MFBitmapDescriptor startIcon; // Icon của điểm bắt đầu
  @Nullable
  private MFBitmapDescriptor endIcon; // Icon của điểm kết thúc
  private String startLabel; // Tiêu đề của điểm bắt đầu
  private String endLabel; // Tiêu đề của điểm kết thúc
  public MFDirectionsRendererOptions()
  public MFDirectionsRendererOptions paths(List<List<MFLocationCoordinate>> paths)
  public MFDirectionsRendererOptions startLocation(@NonNull MFLocationCoordinate position)
  public MFDirectionsRendererOptions endLocation(@NonNull MFLocationCoordinate position)
  public MFDirectionsRendererOptions jsonData(@NonNull String jsonData)
  public MFDirectionsRendererOptions binaryData(@NonNull byte[][] binaryData)
  public MFDirectionsRendererOptions activedIndex(int activedIndex)
  public MFDirectionsRendererOptions activeStrokeColor(@ColorInt int color)
  public MFDirectionsRendererOptions activeOutlineColor(@ColorInt int color)
  public MFDirectionsRendererOptions inactiveStrokeColor(@ColorInt int color)
  public MFDirectionsRendererOptions inactiveOutlineColor(@ColorInt int color)
  public MFDirectionsRendererOptions titleColor(@ColorInt int color)
  public MFDirectionsRendererOptions width(float width)
  public MFDirectionsRendererOptions startIcon(@Nullable MFBitmapDescriptor iconDescriptor)
  public MFDirectionsRendererOptions endIcon(@Nullable MFBitmapDescriptor iconDescriptor)
  public MFDirectionsRendererOptions startLabel(@NonNull String startLabel)
  public MFDirectionsRendererOptions endLabel(@NonNull String endLabel)
  public List<List<MFLocationCoordinate>> getPaths()
  public MFLocationCoordinate getStartLocation()
  public MFLocationCoordinate getEndLocation()
  public String getJsonData()
  public byte[][] getBinaryData()
  public int getActivedIndex()
  @ColorInt
  public int getActiveStrokeColor()
  @ColorInt
  public int getActiveOutlineColor()
  @ColorInt
  public int getInactiveStrokeColor()
  @ColorInt
  public int getInactiveOutlineColor()
  @ColorInt
  public int getTitleColor()
  public float getWidth()
  public MFBitmapDescriptor getStartIcon()
  public MFBitmapDescriptor getEndIcon()
  public String getStartLabel()
  public String getEndLabel()
}

public final class MFDirectionsRenderer {

  private long id;
  private List<List<MFLocationCoordinate>> paths;
  private MFLocationCoordinate startLocation;
  private MFLocationCoordinate endLocation;
  private int activedIndex;
  @ColorInt
  private int activeStrokeColor;
  @ColorInt
  private int activeOutlineColor;
  @ColorInt
  private int inactiveStrokeColor;
  @ColorInt
  private int inactiveOutlineColor;
  @ColorInt
  private int titleColor;
  private float width;
  @Nullable
  private MFBitmapDescriptor startIcon;
  @Nullable
  private MFBitmapDescriptor endIcon;
  private String startLabel;
  private String endLabel;
  private DirectionsRendererDelegate directionsRendererDelegate;

  public MFDirectionsRenderer(@NonNull MFDirectionsRendererOptions options,
                              @NonNull DirectionsRendererDelegate directionsRendererDelegate)
  private void getDataFromJson(@NonNull String jsonData)
  private void getDataFromBinary(@NonNull byte[][] binaryData)
  public List<List<MFLocationCoordinate>> getPaths()
  public MFLocationCoordinate getStartLocation()
  public MFLocationCoordinate getEndLocation()
  public int getActivedIndex()
  @ColorInt
  public int getActiveStrokeColor()
  @ColorInt
  public int getActiveOutlineColor()
  @ColorInt
  public int getInactiveStrokeColor()
  @ColorInt
  public int getInactiveOutlineColor()
  @ColorInt
  public int getTitleColor()
  public float getWidth()
  public MFBitmapDescriptor getStartIcon()
  public MFBitmapDescriptor getEndIcon()
  public String getStartLabel()
  public String getEndLabel()
  public void setPaths(@NonNull List<List<MFLocationCoordinate>> paths)
  public void setStartLocation(@NonNull MFLocationCoordinate startLocation)
  public void setEndLocation(@NonNull MFLocationCoordinate endLocation)
  public void setJsonData(@NonNull String jsonData)
  public void setBinaryData(@NonNull byte[][] binaryData)
  public void setWidth(float width)
  public void setActivedIndex(int activedIndex)
  public void setId(long id)
  public long getId()
  public void remove()
}
```

Các thuộc tính của **MFDirectionsRendererOptions** :

- **paths** : truyền vào một danh sách các list các tọa độ **MFLocationCoordinate** để vẽ các route.
- **startLocation** : truyền vào tọa độ **MFLocationCoordinate** của điểm bắt đầu.
- **endLocation** : truyền vào tọa độ **MFLocationCoordinate** của điểm kết thúc.
- **jsonData** : truyền vào dữ liệu để vẽ các route theo kiểu json.
- **binaryData** : truyền vào dữ liệu để vẽ các route theo kiểu binary.
- **activedIndex** : chỉ định index của route được active khi vẽ nhiều hơn 1 route.
- **activeStrokeColor** : chỉ định màu sắc của route được active theo kiểu **ColorInt**. Giá trị màu mặc định là Color.BLUE.
- **activeOutlineColor** : chỉ định màu sắc outline của route được active theo kiểu **ColorInt**. Giá trị màu mặc định là Color.TRANSPARENT.
- **inactiveStrokeColor** : chỉ định màu sắc của route không được active theo kiểu **ColorInt**. Giá trị màu mặc định là Color.BLACK.
- **inactiveOutlineColor** : chỉ định màu sắc outline của route không được active theo kiểu **ColorInt**. Giá trị màu mặc định là Color.TRANSPARENT.
- **titleColor** : chỉ định màu sắc của text theo kiểu **ColorInt**. Giá trị màu mặc định là Color.Black
- **width** : chỉ định độ rộng của line theo đơn vị point (dp).
- **startIcon** : xác định icon của điểm bắt đầu.
- **endIcon** : xác định icon của điểm kết thúc.
- **startLabel** : chỉ định tên của điểm bắt đầu.
- **endLabel** : chỉ định tên của điểm kết thúc.

### 2. Tạo Directions Renderer

![Directions Renderer](../../resources/7-directions-renderer.png)

> Tạo đối tượng Directions Renderer từ **MFDirectionsRendererOptions**


<!-- tabs:start -->
#### ** Kotlin **
```kotlin
  val directionsRendererOptions = MFDirectionsRendererOptions()
  
  val paths: MutableList<List<MFLocationCoordinate>> = ArrayList()
  val path1: MutableList<MFLocationCoordinate> = ArrayList()
  path1.add(MFLocationCoordinate(16.070508, 108.221204))
  path1.add(MFLocationCoordinate(16.071449, 108.221124))
  path1.add(MFLocationCoordinate(16.071606, 108.222706))

  val path2: MutableList<MFLocationCoordinate> = ArrayList()
  path2.add(MFLocationCoordinate(16.070508, 108.221204))
  path2.add(MFLocationCoordinate(16.070369, 108.222870))
  path2.add(MFLocationCoordinate(16.071606, 108.222706))

  paths.add(path1)
  paths.add(path2)

  directionsRendererOptions.paths(paths)
  directionsRendererOptions.activeStrokeColor(resources.getColor(android.R.color.colorActiveStroke))
  directionsRendererOptions.inactiveStrokeColor(resources.getColor(android.R.color.colorInactiveStroke))
  directionsRendererOptions.activeOutlineColor(Color.BLUE)
  directionsRendererOptions.inactiveOutlineColor(Color.BLACK)
  directionsRendererOptions.width(10f)
  directionsRendererOptions.startLocation(MFLocationCoordinate(16.070526, 108.220990))
  directionsRendererOptions.startLabel("Start")
  directionsRendererOptions.endLocation(MFLocationCoordinate(16.071523, 108.222960))
  directionsRendererOptions.endLabel("End")
  val directionsRenderer = map4D?.addDirectionsRenderer(directionsRendererOptions)
```

#### ** Java **
```java
  MFDirectionsRendererOptions directionsRendererOptions = new MFDirectionsRendererOptions();
  
  List<List<MFLocationCoordinate>> paths = new ArrayList<>();
  List<MFLocationCoordinate> path1 = new ArrayList<>();
  path1.add(new MFLocationCoordinate(16.070508, 108.221204));
  path1.add(new MFLocationCoordinate(16.071449, 108.221124));
  path1.add(new MFLocationCoordinate(16.071606, 108.222706));

  List<MFLocationCoordinate> path2 = new ArrayList<>();
  path2.add(new MFLocationCoordinate(16.070508, 108.221204));
  path2.add(new MFLocationCoordinate(16.070369, 108.222870));
  path2.add(new MFLocationCoordinate(16.071606, 108.222706));

  paths.add(path1);
  paths.add(path2);

  directionsRendererOptions.paths(paths);
  directionsRendererOptions.activeStrokeColor(getResources().getColor(R.color.colorActiveStroke));
  directionsRendererOptions.inactiveStrokeColor(getResources().getColor(R.color.colorInactiveStroke));
  directionsRendererOptions.activeOutlineColor(Color.BLUE);
  directionsRendererOptions.inactiveOutlineColor(Color.BLACK);
  directionsRendererOptions.width(10.f);
  directionsRendererOptions.startLocation(new MFLocationCoordinate(16.070526, 108.220990));
  directionsRendererOptions.startLabel("Start");
  directionsRendererOptions.endLocation(new MFLocationCoordinate(16.071523, 108.222960));
  directionsRendererOptions.endLabel("End");
  directionsRenderer = map4D.addDirectionsRenderer(directionsRendererOptions);
```
<!-- tabs:end -->

Ví dụ trên thì chúng ta tạo một directions Renderer từ 2 danh sách các tọa độ `path1` và `path2` tương ứng với 2 đường đi
với các tùy chỉnh cơ bản.


### 3. Xóa Directions Renderer

> Để xóa Directions Renderer ra khỏi bản đồ ta sử dụng hàm `remove()`

<!-- tabs:start -->
#### ** Kotlin **
```kotlin
  directionsRenderer.remove()
```
#### ** Java **
```java
  directionsRenderer.remove();
```
<!-- tabs:end -->

### 4. Sự kiện click Directions Renderer

- Phát sinh khi người dùng click lên đối tượng `Directions Renderer`

<!-- tabs:start -->

#### ** Kotlin **
```kotlin
    map4D?.setOnDirectionsClickListener { directionsRenderer, index ->
      Log.e("Events", "Click on directions renderer index: $index")
    }
```
#### ** Java **
```java
  map4D.setOnDirectionsClickListener(new Map4D.OnDirectionsClickListener() {
      @Override
      public void onDirectionsClick(MFDirectionsRenderer directionsRenderer, int index) {
          Log.e("Events", "Click on directions renderer index: " + index);
      }
  });
```
<!-- tabs:end -->
* Tham số directionsRenderer sẽ trả về đối tượng directionsRenderer mà người dùng click.
* Tham số index sẽ trả về chỉ số index của list các đường đi mà người dùng click lên.

