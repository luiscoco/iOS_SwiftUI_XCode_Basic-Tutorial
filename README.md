# SwiftUI - Brief Introduction with Samples 

**Apple iOS** is the **operating system** for iPhone, iPad, and other Apple **mobile devices**

SwiftUI is a new way to **build user interfaces UIs** for apps on Apple platforms using Swift code

SwiftUI which is a **declarative framework** you simply tell SwiftUI **what** you want and then let the framework do it for you

## 1. Prerequisites

### 1.1. How to create a Virtual Machine with VirtuaBox for installing Mac Sonoma

See this github repo for a detailed explanation: https://github.com/luiscoco/macOS_Sonoma_VMWare/tree/main

### 1.2. How to install XCode 15 in Mac 



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

```swift
import SwiftUI

struct Weather: Identifiable {
    let id = UUID()
    let day: String
    let temperature: Int
}

struct ContentView: View {
    let weatherData = [
        Weather(day: "Monday", temperature: 22),
        Weather(day: "Tuesday", temperature: 25),
        Weather(day: "Wednesday", temperature: 19),
        Weather(day: "Thursday", temperature: 23),
        Weather(day: "Friday", temperature: 21)
    ]
    
    var body: some View {
        NavigationView {
            List(weatherData) { weather in
                VStack(alignment: .leading) {
                    Text(weather.day)
                        .font(.headline)
                    Text("\(weather.temperature)°C")
                        .font(.subheadline)
                }
            }
            .navigationTitle("Weather Forecast")
        }
    }
}

@main
struct WeatherApp: App {
    var body: some Scene {
        WindowGroup {
            ContentView()
        }
    }
}
```

### 2.5. Form and Data Binding

![image](https://github.com/luiscoco/iOS_SwiftUI_XCode_Basic-Tutorial/assets/32194879/78741189-3aa1-442d-a179-d06ea54e0bfe)

```swift
import SwiftUI

struct ContentView : View {
    @State private var username: String = ""
    @State private var notificationsEnabled: Bool = true
    @State private var selectedColor: Color = .blue
    
    var body: some View {
        NavigationView {
            Form {
                Section(header: Text("Profile")) {
                    TextField("Username", text: $username)
                }
                
                Section(header: Text("Preferences")) {
                    Toggle("Enable Notifications", isOn: $notificationsEnabled)
                    
                    ColorPicker("Favorite Color", selection: $selectedColor)
                }
                
                Section {
                    Button(action: {
                        // Handle save action
                    }) {
                        Text("Save")
                    }
                }
            }
            .navigationTitle("Settings")
        }
    }
}

@main
struct UserSettingsApp: App {
    var body: some Scene {
        WindowGroup {
            UserSettings()
        }
    }
}
```


### 2.6. Animation

```swift
import SwiftUI

struct AnimatedCircle: View {
    @State private var isExpanded = false
    
    var body: some View {
        VStack {
            Circle()
                .frame(width: isExpanded ? 200 : 100, height: isExpanded ? 200 : 100)
                .foregroundColor(isExpanded ? .green : .blue)
                .animation(.easeInOut(duration: 1), value: isExpanded)
            
            Button(action: {
                isExpanded.toggle()
            }) {
                Text("Animate")
                    .padding()
                    .background(Color.black)
                    .foregroundColor(.white)
                    .cornerRadius(10)
            }
        }
    }
}

@main
struct AnimatedCircleApp: App {
    var body: some Scene {
        WindowGroup {
            AnimatedCircle()
        }
    }
}
```


### 2.7. Custom Views

```swift
import SwiftUI

struct CustomCardView: View {
    var title: String
    var subtitle: String
    var backgroundColor: Color
    
    var body: some View {
        VStack(alignment: .leading) {
            Text(title)
                .font(.headline)
                .foregroundColor(.white)
            
            Text(subtitle)
                .font(.subheadline)
                .foregroundColor(.white)
        }
        .padding()
        .background(backgroundColor)
        .cornerRadius(10)
        .shadow(radius: 5)
    }
}

struct ContentView: View {
    var body: some View {
        VStack {
            CustomCardView(title: "Card 1", subtitle: "This is the first card", backgroundColor: .blue)
            CustomCardView(title: "Card 2", subtitle: "This is the second card", backgroundColor: .green)
            CustomCardView(title: "Card 3", subtitle: "This is the third card", backgroundColor: .red)
        }
        .padding()
    }
}

@main
struct CustomViewsApp: App {
    var body: some Scene {
        WindowGroup {
            ContentView()
        }
    }
}
```



### 2.8. Networking with URLSession

```swift
import SwiftUI

struct Post: Codable, Identifiable {
    let id: Int
    let title: String
    let body: String
}

struct ContentView: View {
    @State private var posts = [Post]()
    
    var body: some View {
        NavigationView {
            List(posts) { post in
                VStack(alignment: .leading) {
                    Text(post.title)
                        .font(.headline)
                    Text(post.body)
                        .font(.subheadline)
                }
            }
            .navigationTitle("Posts")
            .onAppear {
                fetchPosts()
            }
        }
    }
    
    func fetchPosts() {
        guard let url = URL(string: "https://jsonplaceholder.typicode.com/posts") else {
            return
        }
        
        URLSession.shared.dataTask(with: url) { data, response, error in
            if let data = data {
                do {
                    let decodedPosts = try JSONDecoder().decode([Post].self, from: data)
                    DispatchQueue.main.async {
                        self.posts = decodedPosts
                    }
                } catch {
                    print("Error decoding data: \(error)")
                }
            }
        }.resume()
    }
}

@main
struct NetworkingApp: App {
    var body: some Scene {
        WindowGroup {
            ContentView()
        }
    }
}
```




### 2.9. Using Core Data


```swift
import SwiftUI
import CoreData

struct ContentView: View {
    @Environment(\.managedObjectContext) private var viewContext
    @FetchRequest(entity: Item.entity(), sortDescriptors: [NSSortDescriptor(keyPath: \Item.timestamp, ascending: true)])
    private var items: FetchedResults<Item>

    @State private var newItemTitle = ""

    var body: some View {
        NavigationView {
            VStack {
                TextField("New item", text: $newItemTitle)
                    .textFieldStyle(RoundedBorderTextFieldStyle())
                    .padding()

                Button(action: addItem) {
                    Text("Add")
                        .padding()
                        .background(Color.blue)
                        .foregroundColor(.white)
                        .cornerRadius(10)
                }

                List {
                    ForEach(items) { item in
                        Text(item.title ?? "Untitled")
                    }
                    .onDelete(perform: deleteItems)
                }
            }
            .navigationTitle("Core Data Items")
        }
    }

    private func addItem() {
        withAnimation {
            let newItem = Item(context: viewContext)
            newItem.timestamp = Date()
            newItem.title = newItemTitle
            newItemTitle = ""

            do {
                try viewContext.save()
            } catch {
                // Handle error
            }
        }
    }

    private func deleteItems(offsets: IndexSet) {
        withAnimation {
            offsets.map { items[$0] }.forEach(viewContext.delete)

            do {
                try viewContext.save()
            } catch {
                // Handle error
            }
        }
    }
}

@main
struct CoreDataApp: App {
    let persistenceController = PersistenceController.shared

    var body: some Scene {
        WindowGroup {
            ContentView()
                .environment(\.managedObjectContext, persistenceController.container.viewContext)
        }
    }
}

struct PersistenceController {
    static let shared = PersistenceController()

    let container: NSPersistentContainer

    init() {
        container = NSPersistentContainer(name: "YourModelName")
        container.loadPersistentStores { storeDescription, error in
            if let error = error as NSError? {
                // Handle error
            }
        }
    }
}
```








## 3. Additional information

https://en.wikipedia.org/wiki/SwiftUI

https://developer.apple.com/tutorials/swiftui-concepts

https://developer.apple.com/tutorials/swiftui

https://developer.apple.com/tutorials/sample-apps

https://github.com/ArisGuimera/iOS-Expert

https://www.hackingwithswift.com/quick-start/swiftui

https://www.youtube.com/watch?v=f6WtmTBFNGM&t=10376s

**CURSO: SWIFT y SWIFTUI desde CERO en ESPAÑOL - Programación IOS - TUTORIAL XCODE**:

https://www.youtube.com/watch?v=f6WtmTBFNGM&list=PL8ie04dqq7_MeCR8iYIy_eumrYK7JzuPJ
