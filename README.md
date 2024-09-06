# USDZARCamera

A SwiftUI USDZ Object Scanner for Capturing Real Life Objects and transforming to USDZ file using Photogrametry. No need to export images and create models separately.

## Requirements

- iPhone or iPad with a LiDAR Scanner and an A14 Bionic chip or later
- iOS or iPadOS 17 or later

## Installation

### Swift Package Manager
- File > Swift Packages > Add Package Dependency
- Add https://github.com/JeckyKukadiya/USDZARCamera.git

You must add `Privacy - Camera Usage Description` permission in your App Info.plist to use the scanner.  

## Usage

Initialize USDZARCamera passing the completion callback. The completion contains a parameter for the URL where it stored the USDZ file.

```swift
import SwiftUI
import USDZSARCamera

@main
struct SampleApp: App {

    @State var isScanObjectPresenting = false
    @State var url: URL?
    
    var body: some Scene {
        WindowGroup {
            VStack {
                
                Button("Scan Object") {
                    isScanObjectPresenting = true
                }
                
                if let url {
                    Text(url.absoluteString)
                }
                
            }
            .sheet(isPresented: $isScanObjectPresenting, content: {
                USDZScanner { url in
                    self.url = url
                    isScanObjectPresenting = false
                }
            })
        }
    }
}
```
