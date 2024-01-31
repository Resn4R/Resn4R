## Hi there 👋

### Welcome to my Dev Playground 👨🏼‍💻
Hey there! I'm Vito, a passionate and enthusiastic Swift developer excited about building amazing mobile experiences. 
Welcome to my GitHub repository, where I showcase my projects, skills, and journey in the development world. 
Occasionally (aka a lot), I will also upload personal test apps to try out frameworks and features or just to have fun with new practices as I discover them.

## About Me 🙋🏼‍♂️
- 🧩 Loves cracking and solving puzzles
- 📱 Exploring the wonders of iOS development
- 🎓 Graduated from the Istituto Tecnico Industriale Statale "L. Da Vinci" in Computer Science 
- 📚 Eager to contribute and learn from the vibrant iOS development community

# Projects

## The Brewtherhood Loyalty Card
This project represents a passionate exploration of iOS app development using Swift, SwiftUI and other frameworks. As an aspiring developer eager to learn and grow, this tech demo showcases the application of newly acquired skills and the enthusiasm to create an innovative loyalty card experience for users. Customers can earn points, rewards, and special offers through this app, encouraging repeat business and promoting brand loyalty.

### Features
- **Digital Loyalty Cards**: Replace traditional paper-based loyalty cards with a digital version through the usage of a QR code scanner with dedicated QR codes to add stamps and redeem free items.
- **Points Tracking**: Keep track of points earned for purchases and activities, making it easy for customers to see their progress.
- **Rewards Redemption**: Enable users to redeem their points for discounts and free items
- **Store Locator**: Integrate a store locator feature, allowing users to find nearby stores participating in the loyalty program.

### Technologies Used
- Swift
- SwiftUI
- SwiftData
- MapKit
- AVFoundations

### **Code Sample**
  This is how, upon opening of the app, SwiftData checks if the database is populated. If it is, the context loads the data but if the database is empty, the context will just add an empty stampcard.
```swift
    @MainActor
    let appContainer: ModelContainer = {
        do {
            let container = try ModelContainer(for: StampCard.self)
            
            var stampCardFetchDescriptor = FetchDescriptor<StampCard>()
            stampCardFetchDescriptor.fetchLimit = 1
            
            guard try container.mainContext.fetch(stampCardFetchDescriptor).count == 0 else { return container }
            
            container.mainContext.insert(StampCard())
            return container
        }
        catch { fatalError("Failed to create container") }
    }()
```

## Lorem Picsum
This is a personal test to explore Swift's async await as well as AsyncImage. Once implemented I decided to experiment with storage solutions and how to save Image data from the internet to SwiftData's external storage.

- **Key Features:**
  - Loads a random picture from the Lorem Picsum website
  - Apply a filter to the image (blur / gray scale)
  - Save with SwiftData and see your saved pics through Gallery

- **Technologies Used:**
  - Swift
  - SwiftUI
  - SwiftData
  - Swift Concurrency

### **Code Sample**
  ```swift
              VStack{
                AsyncImage(url: URL(string: "https://picsum.photos/id/\(id)/400/300/?\(imageModifier)"), scale: 1) { phase in
                    switch phase {
                        case .empty: ProgressView()
                        case .success(let loadedImage): loadedImage
                        case .failure: Text("Failed to load the image. Try Again.")
                        @unknown default: EmptyView()
                    }
                }
                Picker("image modifier", selection: $imageModifier) {
                    ForEach(imageModifiers, id: \.self) {
                        Text($0)
                    }
                }
                .pickerStyle(.palette)
                .padding()

                Group {
                    Button("Save to album"){
                        Task {
                            guard let url = URL(string: "https://picsum.photos/id/\(id)/400/300/?\(imageModifier)") 
                            else { fatalError() }
                            
                            do {
                                let (data, _) = try await URLSession.shared.data(from: url)
                                
                                let pic = RandyRandyPic(image: data)
                                modelContext.insert(pic)
                                try? modelContext.save()
                            }
                            catch {
                                print("invalid data.")
                            }
                            print("image downloaded and saved successfully.")
                        }
                    }
  ```

## Skills

- **Languages:**
  - Swift (Main)
  - Some Python
  - some HTML
  - Java (used for codewars katas, no git used)

- **Frameworks/Libraries:**
- Swift:
  - UIKit
  - SwiftUI
  - SwiftData
  - UserNotifications
  - LocalAuthentication
  - Metal
  - AVFoundations
  - MapKit
  - XCTest
  - CoreLocation
  - CoreImage / .CIFilterBuiltins
  - PhotosUI
 
- Python:
  - requests
  - datetime
  - sqlite3
  - numpy
  - panda
  - matplotlib
  - flask
  - janji2

- **Tools:**
  - Xcode
  - Notepad++
  - Fork
  - Trello
  - Py Editor
  - Git
  - RocketSim
  - Maccy
  - Warp

- **Designs and Architectures:**
  - Builder
  - Factory Method
  - Adapter
  - MVVM
  - MVC


## Learning Journey 📚📖
I'm on a continuous learning journey, exploring new concepts and technologies. My goal is to become a proficient developer, and I'm excited about every challenge that comes my way.
Although I have no working experience of my own, I am dedicated to learn as much as I can to deliver quality services and quality code. 
The hope is to find employment as a developer with a business who is willing to invest in new talent and believes in the benefits I will bring to the table.

## Connect with Me 🔗
- 💼 LinkedIn:([Vito Borghi](https://www.linkedin.com/in/vito-borghi/))
- 👨🏼‍💻 CodeWars: [Resn4R](https://www.codewars.com/users/Resn4R)
- 📫 Email: purview-joust.0x@icloud.com

## Let's Code Together! 👨🏼‍💻👨🏼‍💻👨🏼‍💻
I'm always open to collaboration, learning opportunities, and connecting with fellow devs. Feel free to explore my projects, ask questions, or reach out for a chat. Let's build something amazing together! 🚀
