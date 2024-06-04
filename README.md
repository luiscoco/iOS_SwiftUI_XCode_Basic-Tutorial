# iOS  SwiftUI lesson1

https://developer.apple.com/tutorials/swiftui-concepts

https://developer.apple.com/tutorials/swiftui

https://developer.apple.com/tutorials/sample-apps

https://github.com/ArisGuimera/iOS-Expert

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

![image](https://github.com/luiscoco/iOS_SwiftUI_XCode_lesson1/assets/32194879/7c708ee9-26f0-4fa1-8845-280c0f14c03c)

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

![image](https://github.com/luiscoco/iOS_SwiftUI_XCode_lesson1/assets/32194879/76c521bf-63c5-4022-819a-b288884a17a2)

### 2.2. Simple Counter App

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

### 2.3. TodoList App

This app demonstrates how to use lists and manage data with a simple todo list

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



### 2.4. 




### 2.4. 




### 2.5. 



## 3. 
