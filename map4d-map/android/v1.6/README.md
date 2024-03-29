# Map4dMap Android SDK
[![map4d](https://img.shields.io/badge/map4d-map-orange)](https://map4d.vn/)
[![platform](https://img.shields.io/badge/platform-android-brightgreen.svg)](https://www.android.com/)
[![maven](https://img.shields.io/maven-metadata/v?metadataUrl=https%3A%2F%2Fpackages.map4d.vn%2Frepository%2Fmaven-public%2Fvn%2Fmap4d%2FMap4dMap%2Fmaven-metadata.xml)](https://map4d.vn/)

Map4dMap Android SDK for Android, written in C/C++, Java.  

> Map4D Android SDK cho phép bạn tùy chỉnh bản đồ với nội dung để hiển thị trên thiết bị android hỗ trợ opengl 2.0   
Map4D Android SDK không chỉ mang hình ảnh thực tế lên trên bản đồ 3D, ngoài ra còn cho phép tương tác và điều chỉnh các đối tượng 3D của bạn  

[![Map4D Android SDK](../resources/overView.png)](https://map4d.vn) 

## Installation

Nếu dự án của bạn dùng Gradle thì trước hết cần khai báo url cho maven trong file gradle project.

```xml
allprojects {
    repositories {
        maven {
            url = "https://packages.map4d.vn/repository/maven-public"
        }
    }
}
```

Thêm vào dependencies:

```xml
dependencies {
  implementation 'vn.map4d:Map4dTypes:1.1.0'
  implementation 'vn.map4d:Map4dMap:1.6.0'
}
```

## Using

1. Provide access key

```xml
<?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
  package="vn.map4d.simplemap">
  <application
    android:theme="@style/AppTheme">
    <meta-data
      android:name="vn.map4d.map.ACCESS_KEY"
      android:value="TYPE_YOUR_KEY_HERE"/>
  </application>
  <uses-permission android:name="android.permission.INTERNET" />
  <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
  <uses-permission android:name="android.permission.ACCESS_FINE_LOCATION" />
</manifest>

```

2. Create layout

```xml
<vn.map4d.map.core.MFMapView
  android:id="@+id/mapView"
  android:layout_width="wrap_content"
  android:layout_height="wrap_content"
/>
```
3. Working với map view

<!-- tabs:start -->
#### ** Java **

```java
public class MainActivity extends AppCompatActivity implements OnMapReadyCallback{ 
    
    private MFMapView mapView;
	private Map4D map4D;
  
    @Override
    protected void onCreate(Bundle savedInstanceState) { 
        super.onCreate(savedInstanceState);
        setContentView(R.layout.simple3d_map_activity);
        mapView = findViewById(R.id.map3D);
        mapView.getMapAsync(this); 
    }
  
    @Override
    public void onMapReady(Map4D map4D) { 
        map4D.enable3DMode(true);
		// Your code
    }
      
    @Override
    protected void onDestroy() { 
        mapView.onDestroy(); 
        super.onDestroy();
    }
}
```

#### ** Kotlin **

```kotlin
import vn.map4d.map.core.Map4D
import vn.map4d.map.core.OnMapReadyCallback

class MainActivity : AppCompatActivity(), OnMapReadyCallback {

	private var map4D: Map4D? = null

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)
        mapView?.getMapAsync(this)
    }

    override fun onMapReady(map4D: Map4D?) {
        map4D?.enable3DMode(true)
        // Your code
    }
    
     override fun onDestroy() {
        mapView?.onDestroy()
        super.onDestroy()
     }
}
```
<!-- tabs:end -->

> **Chú ý:** Khi dùng MFMapView thì cần phải destroy view để tránh trường hợp leak memory
