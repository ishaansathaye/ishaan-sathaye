---
layout: default
---

# About me

I started my journey as a coder at the age of 5, beginning with the language of Bloodshed Pascal. I began to learn Java when I was 9, initially taking a course at Stanford. Java has become a fundamental language for me, since I use it in my school's robotics team. I had my first exposure to the language of the future-Python-by learning how to code using the Raspberry Pi. This  would become the basis of my major projects, including a attendance system I developed for my school and a temeprature sensor. In addition, I have learned Xcode aided by the Apple's language Swift to develop my own apps for all iOS platforms. My coding language repertoire of Python and Xcode will allow me to use app development to enhance my machine learning skills.


* * *


# Xcode (Swift): iOS App Development

[Xcode 11](https://developer.apple.com/xcode/). includes everything to create amazing apps and to bring apps to even more devices. Takes advantage of SwiftUI, an all-new user interface framework with a declarative Swift syntax.


## Places

> App that allows a user to record places to visit by long pressing on the map. App is built with two view controllers: one that controls the table view, where all the favorite places can be seen and another view controller for controlling the map. The map controller allows the map to find the user's location and center it and then find the coorindates for their favorite place and center it on the screen at anytime. At the bottom of the map is a map selector, which controlled by a segmented contol. This allows the user to pick which type of map they want: satellite, standard, and hybrid. In addition, there is a delete function to remove favorite places when not needed. As always there is permanent storage so the user will not lose their data everytime the app is closed and reopened. The app is complete with a launch screen and assets.

> Project repository: [Places](https://github.com/ishaansathaye/xcode/tree/master/Places)

**APP DEMO:**
[![Places App Demo (Xcode x Swift)](https://i.imgur.com/vsBmPtv.png)](https://youtu.be/TncjzwXr_20 "Places App Demo (Xcode x Swift)")


## Tic Tac Toe

> Traditional game built on iOS 12.2. Allows two players to play on a single device with displays checking and showing win and tie conditions. Also included a play again button to allow players to reset their game after a tie or win. Uses animation to show a win or tie labels. The app is complete with a launch screen and app icon.

> Project repository: [Tic Tac Toe](https://github.com/ishaansathaye/xcode/tree/master/TicTacToe)

**APP DEMO:**
[![Tic Tac Toe App Demo (Xcode x Swift)](https://i.imgur.com/pXpHdIe.png)](https://youtu.be/WkLzj1ktC4U "Tic Tac Toe App Demo (Xcode x Swift)")


## Animations

> App animates an image frame by frame, using grow/decrease, fade-in, movement animations. This app is a segue to creating animation used in games on iOS. By using the "CG" library, I am able to alter the image's location before the app opens. So when the app is opened by the user, the animation would start. By using the Timer library of Siwft I am able to call a function using a timer obejct to update the image. The function would update the frame one by one, and also a button is added to stop and start the animation of the image.

> Project repository: [Animations](https://github.com/ishaansathaye/xcode/tree/master/Animations)

Image animation frame by frame: 
```swift
@IBAction func updateImage(_ sender: Any) {
        if isAnimating == true {
            timer.invalidate()
            isAnimating = false            
        } else {          
            timer = Timer.scheduledTimer(timeInterval: 0.1, target: self, selector: #selector(doAnimation), userInfo: nil, repeats: true)
            isAnimating = true
        }  
}
override func viewDidLoad() {
    super.viewDidLoad()
    timer = Timer.scheduledTimer(timeInterval: 0.1, target: self, selector: #selector(doAnimation), userInfo: nil,               repeats: true) // Set a timer to call the function to animate
}    
@objc func doAnimation(){        
    pandaImage.image = UIImage(named: "frame\(counter).png") // Change frame        
    counter += 1   
    if counter == 8 {
        counter = 1
    }
}
```        

Image animation as a whole: 
```swift
override func viewDidLayoutSubviews() { // Before app opened
    pandaImage.center = CGPoint(x: pandaImage.center.x - 400, y: pandaImage.center.y) // Slide Animation
    pandaImage.alpha = 0 // Fade animation
}
override func viewDidAppear(_ animated: Bool) { // After app opened
    UIView.animate(withDuration: 1, animations: { () -> Void in
        self.pandaImage.center = CGPoint(x: self.pandaImage.center.x + 400, y: self.pandaImage.center.y) // Slide Animation
        self.pandaImage.alpha = 1 // Fade animation
    // Grow/Decrease Animation
        self.pandaImage?.transform = CGAffineTransform(scaleX: 0.0, y: 0.0) // Decrease size animation
    }){ (_ finished: Bool) in
        UIView.animate(withDuration: 1, animations: {
            self.pandaImage?.transform = CGAffineTransform(scaleX: 2, y: 2)// Increase size animation
            self.pandaImage?.center = CGPoint(x: self.pandaImage.center.x - 30, y: self.pandaImage.center.y) // Move image
       })
    } 
}
```

## What's the Weather?

> The main aspect of this app is to access a website's data and display parts that are needed in an app. Using the website weather-forecast.com, the app takes the weather that will come for the next three days and displays it as text into the app. The user enters the city of their choice and then the app will take that city and put it into the URL. After that the program will splice the parts that are needed using keyword: "</span>" and take the data after that. The library being used in this app is URLSession which will allow me to access a url's data. A new concept that is used in this app is asynchronous code, where instead of waiting for URLSession to access the data and then display it, the two parts of the program will happen at the same time.

> Project Repository: [What's the Weather?](https://github.com/ishaansathaye/xcode/tree/master/What's%20the%20Weather)

Asynchronous Code:
```swift
DispatchQueue.main.async { // runs this code when information present instead of waiting for queue
        if urlError == true {
                self.showError() // shows an error if data not available
        } else {
                self.resultLabel.text = "\(weather)" // displays the weather of that city
        }
}
```

**APP DEMO:**
[![What's the Weather App Demo (Xcode x Swift)](https://i.imgur.com/XccJwOi.png)](https://youtu.be/zGe4nkyu9d4 "What's the Weather App Demo (Xcode x Swift)")


## To Do List

> This app allows a user to add items to their list and then jsut delete them when they finish the item on their list. The app uses segues and permanent storage to make the app efficient and personalized. Segues allow a user to go to different pages when doing different actions. The first view controller controls the making of the table and the cells inside the table, and it also creates an array to put the user's items into. The second view controller is where the user can enter toDos into their list, after that the array is appended. Permanent Storage is put into this app so when the app is refreshed or closed, their data would not be erased. In the second view controller the item is stored using the library "User Defaults" while in the first one the data is called when the app is opened.

> Project Repository: [To Do List](https://github.com/ishaansathaye/xcode/tree/master/To%20Do%20List)

Storing the data when item entered:
```swift
@IBAction func addItem(_ sender: Any) {
        toDoList.append(item.text!) // adds item to the array
        item.text = "" // sets the textField back to empty
        UserDefaults.standard.setValue(toDoList, forKey: "toDoList") // stores the entire data in the array
    }
```

Retrieving the data by calling the key: 
```swift
override func viewDidLoad() {
        super.viewDidLoad()
        if UserDefaults.standard.object(forKey: "toDoList") != nil { //checks if the list is not empty
            toDoList = UserDefaults.standard.object(forKey: "toDoList") as! [String] // retrieves the data using the key
        }
    }
```

**APP DEMO:**
[![To Do List App Demo (Xcode x Swift)](https://i.imgur.com/brRwMHA.png)](https://youtu.be/I-Gnq3FBZuE "To Do List App Demo (Xcode x Swift)")


## Cat Years (My First App)

> My first app was simple. I took in the age of the user's cat in years using a text field. Then I took that value and multiplied it by 7 to get the cat's age in years. I then displayed this output in a label on the UI. I ran the app using the Xcode Simulator, where I can run my app on iOS, macOS, and iPadOS devices.

> Project repository: [Cat Years](https://github.com/ishaansathaye/xcode/tree/master/Cat%20Years)

















<!--- #### Header 4

*   This is an unordered list following a header.
*   This is an unordered list following a header.
*   This is an unordered list following a header.

##### Header 5

1.  This is an ordered list following a header.
2.  This is an ordered list following a header.
3.  This is an ordered list following a header.

###### Header 6

| head1        | head two          | three |
|:-------------|:------------------|:------|
| ok           | good swedish fish | nice  |
| out of stock | good and plenty   | nice  |
| ok           | good `oreos`      | hmm   |
| ok           | good `zoute` drop | yumm  |

### There's a horizontal rule below this.

* * *

### Here is an unordered list:

*   Item foo
*   Item bar
*   Item baz
*   Item zip

### And an ordered list:

1.  Item one
1.  Item two
1.  Item three
1.  Item four

### And a nested list:

- level 1 item
  - level 2 item
  - level 2 item
    - level 3 item
    - level 3 item
- level 1 item
  - level 2 item
  - level 2 item
  - level 2 item
- level 1 item
  - level 2 item
  - level 2 item
- level 1 item

### Small image

![Octocat](https://github.githubassets.com/images/icons/emoji/octocat.png)

### Large image

![Branching](https://guides.github.com/activities/hello-world/branching.png)


### Definition lists can be used with HTML syntax.

<dl>
<dt>Name</dt>
<dd>Godzilla</dd>
<dt>Born</dt>
<dd>1952</dd>
<dt>Birthplace</dt>
<dd>Japan</dd>
<dt>Color</dt>
<dd>Green</dd>
</dl>

```
Long, single-line code blocks should not wrap. They should horizontally scroll if they are too long. This line should be long enough to demonstrate this.
```

```
The final element.
```
--->
