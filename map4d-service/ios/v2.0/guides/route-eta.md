# Route ETA

> Tính toán thời gian dự kiến các đường đi giữa các địa điểm.

### Usage

- Service: [MFDirectionsService](reference/directions-service.md)
- Params: [MFRouteETAParams](reference/route-eta-params.md)
- Return: [MFServiceTask](reference/service-task.md)
- Callback:
  + Result: Array of [MFRouteETAResult](reference/route-eta-result.md)
  + Error: [MFServiceError](reference/service-error.md)

### Example

<!-- tabs:start -->
#### ** Swift **
```swift
let origins = [
  MFLocationComponent(latitude: 16.024634, longitude: 108.209217, alias: "A"),
  MFLocationComponent(latitude: 16.039173, longitude: 108.210912, alias: "B")
]
let destination = MFLocationComponent(latitude: 16.020179, longitude: 108.211212)
let params = MFRouteETAParams(origins: origins, destination: destination, mode: .motorcycle, weighting: .shortest)
let service = MFDirectionsService()

service.fetchRouteETA(with: params) { results, error in
  guard let results = results else {
    print("Error: \(error!.message)")
    return
  }

  print("Results count: \(results.count)")
}
```

#### ** Objective-C **
```objc
NSArray<MFLocationComponent *> *origins = @[
  [[MFLocationComponent alloc] initWithLatitude:16.024634 longitude: 108.209217],
  [[MFLocationComponent alloc] initWithLatitude:16.039173 longitude: 108.210912]
];
MFLocationComponent *destination = [[MFLocationComponent alloc] initWithLatitude:16.020179 longitude: 108.211212];
MFRouteETAParams *params = [[MFRouteETAParams alloc] initWithOrigins:origins destination:destination];
MFPlacesService* service = [[MFDirectionsService alloc] init];

[service fetchRouteETAWithParams:params
               completionHandler:^(NSArray<id<MFRouteETAResult>> * _Nullable results, id<MFServiceError>  _Nullable error) {
  if (error != nil) {
    NSLog(@"Error code: %@, message: %@", error.code, error.message);
  }
  
  if (results != nil) {
    NSLog(@"Results count: %lu", results.count);
  }
}];
```
<!-- tabs:end -->
