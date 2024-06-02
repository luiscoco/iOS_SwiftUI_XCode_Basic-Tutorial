# iOS  SwiftUI lesson1

https://developer.apple.com/tutorials/swiftui

https://github.com/ArisGuimera/iOS-Expert

**CURSO: SWIFT y SWIFTUI desde CERO en ESPAÑOL - Programación IOS - TUTORIAL XCODE**:

https://www.youtube.com/watch?v=f6WtmTBFNGM&list=PL8ie04dqq7_MeCR8iYIy_eumrYK7JzuPJ

## 1. Prerequisites

### 1.1. How to create a Virtual Machine with VirtuaBox for installing Mac iOS

Install macOS in VirtualBox on Windows PC [Intel & AMD]: https://www.youtube.com/watch?v=vQJrM7HqezQ

After instaling Mac **Big Sur 11** on our VM in Window PC we can upgrade it to Mac **Sonoma 14** 

## 1.2. How to install XCode 15 in Mac 



## 2. Learning by doing applications


### 2.1. Simple Counter App
This app will help you understand the basics of state management in SwiftUI.

```swift
import SwiftUI

struct ContentView: View {
    @State private var counter = 0
    
    var body: some View {
        VStack {
            Text("Counter: \(counter)")
                .font(.largeTitle)
                .padding()
            
            HStack {
                Button(action: {
                    counter -= 1
                }) {
                    Text("-")
                        .font(.largeTitle)
                        .padding()
                        .background(Color.red)
                        .foregroundColor(.white)
                        .cornerRadius(10)
                }
                
                Button(action: {
                    counter += 1
                }) {
                    Text("+")
                        .font(.largeTitle)
                        .padding()
                        .background(Color.green)
                        .foregroundColor(.white)
                        .cornerRadius(10)
                }
            }
        }
    }
}

@main
struct CounterApp: App {
    var body: some Scene {
        WindowGroup {
            ContentView()
        }
    }
}
```

### 2.2. 



### 2.3. 




### 2.4. 




### 2.5. 



## 3. 
