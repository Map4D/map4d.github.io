# Graph Route

> Tìm biểu đồ tuyến đường giữa các địa điểm.

### Usage

- Service: [MFDirectionsService](reference/directions-service.md)
- Params: [MFGraphRouteParams](reference/graph-route-params.md)
- Return: [MFServiceTask](reference/service-task.md)
- Callback:
  + Result: Array of [MFGraphRouteResult](reference/graph-route-result.md)
  + Error: [MFServiceError](reference/service-error.md)

### Example

<!-- tabs:start -->
#### ** Swift **
```swift
let params = MFGraphRouteParams(locations: [
  MFLocationComponent(coordinate: CLLocationCoordinate2DMake(16.039173, 108.210912)),
  MFLocationComponent(coordinate: CLLocationCoordinate2DMake(16.044597, 108.217263)),
  MFLocationComponent(coordinate: CLLocationCoordinate2DMake(16.082598, 108.221989))
])
let service = MFDirectionsService()

service.fetchGraphRoute(with: params) { results, error in
  guard let results = results else {
    print("Error: \(error!.message)")
    return
  }

  print("Results count: \(results.count)")
}
```

#### ** Objective-C **
```objc
NSArray *locations = @[
  [[MFLocationComponent alloc] initWithLatitude:16.039173 longitude:108.210912],
  [[MFLocationComponent alloc] initWithLatitude:16.044597 longitude:108.217263]
];
MFGraphRouteParams *params = [[MFGraphRouteParams alloc] initWithLocations:locations
                                                                      mode:MFTravelModeBike
                                                                 weighting:MFRouteWeightingShortest];
MFPlacesService* service = [[MFDirectionsService alloc] init];
[service fetchGraphRouteWithParams:params
                 completionHandler:^(NSArray<id<MFGraphRouteResult>> * _Nullable results, id<MFServiceError>  _Nullable error) {
  if (error != nil) {
    NSLog(@"Error code: %@, message: %@", error.code, error.message);
  }
  
  if (results != nil) {
    NSLog(@"Results count: %lu", results.count);
  }
}];
```
<!-- tabs:end -->
