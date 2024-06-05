# SwiftUI - Brief Introduction with Samples 

**Apple iOS** is the **operating system** for iPhone, iPad, and other Apple **mobile devices**

**SwiftUI** is a new way to **build user interfaces UIs** for apps on Apple platforms using **Swift** code

**SwiftUI** which is a **declarative framework**

This means that instead of writing code to control every little action, you simply tell SwiftUI **what** you want and then let the framework do it for you

https://en.wikipedia.org/wiki/SwiftUI

https://developer.apple.com/tutorials/swiftui-concepts

https://developer.apple.com/tutorials/swiftui

https://developer.apple.com/tutorials/sample-apps

https://github.com/ArisGuimera/iOS-Expert

https://www.hackingwithswift.com/quick-start/swiftui

https://www.youtube.com/watch?v=f6WtmTBFNGM&t=10376s

**CURSO: SWIFT y SWIFTUI desde CERO en ESPAÑOL - Programación IOS - TUTORIAL XCODE**:

https://www.youtube.com/watch?v=f6WtmTBFNGM&list=PL8ie04dqq7_MeCR8iYIy_eumrYK7JzuPJ

## 1. Prerequisites

### 1.1. How to create a Virtual Machine with VirtuaBox for installing Mac Sonoma



## 1.2. How to install XCode 15 in Mac 



## 2. Learning by doing applications

### 2.1. My First Application with SwiftUI

See the application running in the **IPhone simulator** 

![image](https://github.com/luiscoco/iOS_SwiftUI_XCode_lesson1/assets/32194879/121bb917-9bbd-49ed-9327-898c300869ea)

See **myfirstapp** code

```swift
import SwiftUI

@main
struct myfirstappApp: App {
    var body: some Scene {
        WindowGroup {
            ContentView()
        }
    }
}
```

See the **ContentView** code

```swift
import SwiftUI

struct ContentView: View {
    var body: some View {
        VStack {
            Image(systemName: "globe")
                .imageScale(.large)
                .foregroundStyle(.tint)
            Text("Hello, world!")
        }
        .padding()
    }
}

#Preview {
    ContentView()
}
```

### 2.2. Simple Counter App (State management)

This app will help you understand the basics of **state management** in SwiftUI

![image](https://github.com/luiscoco/iOS_SwiftUI_XCode_lesson1/assets/32194879/89c7e5c8-fae0-4905-aa9f-9858ce9dacdd)

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

### 2.3. TodoList App (List)

This app demonstrates how to use lists and manage data with a simple todo list

![image](https://github.com/luiscoco/iOS_SwiftUI_XCode_lesson1/assets/32194879/e2a76bee-4aa5-4280-ad57-e77b5db9e31a)

```swift
import SwiftUI

struct TodoItem: Identifiable {
    let id = UUID()
    let title: String
}

struct ContentView: View {
    @State private var items = [TodoItem]()
    @State private var newItemTitle = ""
    
    var body: some View {
        NavigationView {
            VStack {
                HStack {
                    TextField("New item", text: $newItemTitle)
                        .textFieldStyle(RoundedBorderTextFieldStyle())
                        .padding()
                    
                    Button(action: {
                        let newItem = TodoItem(title: newItemTitle)
                        items.append(newItem)
                        newItemTitle = ""
                    }) {
                        Text("Add")
                            .padding()
                            .background(Color.blue)
                            .foregroundColor(.white)
                            .cornerRadius(10)
                    }
                }
                
                List(items) { item in
                    Text(item.title)
                }
            }
            .navigationTitle("Todo List")
        }
    }
}
```

### 2.4. Weather App (Fetch mock data)

This app shows how to fetch and display data from a web API. For simplicity, we will use mock data

![image](https://github.com/luiscoco/iOS_SwiftUI_XCode_lesson1/assets/32194879/2d22aa93-a590-4e69-b663-6cf4173a1ebb)



### 2.5. 




### 2.6. 



## 3. 
