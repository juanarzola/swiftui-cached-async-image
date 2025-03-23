# SwiftUI CachedAsyncImage 🗃️

`CachedAsyncImage` is `AsyncImage`, but with cache capabilities. 


## Usage

`CachedAsyncImage` has the exact same API and behavior as `AsyncImage`, so you just have to change this:
```swift
AsyncImage(url: logoURL)
```
to this:
```swift
CachedAsyncImage(url: logoURL)
```

In addition to `AsyncImage` initializers, you have the possibilities to specify the cache you want to use (by default `URLCache.shared` is used), and to use `URLRequest` instead of `URL`:
```swift
CachedAsyncImage(urlRequest: logoURLRequest, urlCache: .imageCache)
```

```swift
// URLCache+imageCache.swift

extension URLCache {
    
    static let imageCache = URLCache(memoryCapacity: 512_000_000, diskCapacity: 10_000_000_000)
}
```

Remember when setting the cache the response (in this case our image) must be no larger than about 5% of the disk cache (See [this discussion](https://developer.apple.com/documentation/foundation/nsurlsessiondatadelegate/1411612-urlsession#discussion)).

You can also modify the `URLSessionConfiguration` used by `CachedAsyncImage` via `URLSessionConfiguration.cachedAsyncImage`:

```swift
URLSessionConfiguration.cachedAsyncImage.protocolClasses = [MyContentProtocol.self]
```

## Installation

1. In Xcode, open your project and navigate to **File** → **Swift Packages** → **Add Package Dependency...**
2. Paste the repository URL (`https://github.com/lorenzofiamingo/swiftui-cached-async-image`) and click **Next**.
3. Click **Finish**.


## Other projects

[SwiftUI VariadicViews 🥞](https://github.com/lorenzofiamingo/swiftui-variadic-views)

[SwiftUI AsyncButton 🖲️](https://github.com/lorenzofiamingo/swiftui-async-button)

[SwiftUI MapItemPicker 🗺️](https://github.com/lorenzofiamingo/swiftui-map-item-picker)

[SwiftUI PhotosPicker 🌇](https://github.com/lorenzofiamingo/swiftui-photos-picker)

[SwiftUI VerticalTabView 🔝](https://github.com/lorenzofiamingo/swiftui-vertical-tab-view)

[SwiftUI SharedObject 🍱](https://github.com/lorenzofiamingo/swiftui-shared-object)
