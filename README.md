![SSASideMenu](https://github.com/SSA111/SSASideMenu/blob/master/SSASideMenuCover.png)

[![](http://img.shields.io/badge/iOS-8.0%2B-blue.svg)]() [![](http://img.shields.io/badge/Swift-3.0-blue.svg)]()

SSASideMenu is a reimplementation of
[romaonthego/RESideMenu](https://github.com/romaonthego/RESideMenu) in
Swift. A iOS 7/8 style side menu with parallax effect.  

![](https://github.com/SSA111/SSASideMenu/blob/master/LeftDemo.gif)
![](https://github.com/SSA111/SSASideMenu/blob/master/RightDemo.gif)


###Usage

```swift
      func application(_ application: UIApplication, didFinishLaunchingWithOptions launchOptions: [UIApplicationLaunchOptionsKey: Any]?) -> Bool {

      window = UIWindow(frame: UIScreen.main.bounds)

        //MARK : Setup SSASideMenu

        let sideMenu = SSASideMenu(contentViewController: UINavigationController(rootViewController: FirstViewController()), leftMenuViewController: LeftMenuViewController(), rightMenuViewController: RightMenuViewController())
        sideMenu.backgroundImage = UIImage(named: "Background.jpg")
        sideMenu.configure(SSASideMenu.MenuViewEffect(fade: true, scale: true, scaleBackground: false))
        sideMenu.configure(SSASideMenu.ContentViewEffect(alpha: 1.0, scale: 0.7))
        sideMenu.configure(SSASideMenu.ContentViewShadow(enabled: true, color: UIColor.black, opacity: 0.6, radius: 6.0))
        sideMenu.delegate = self

        window?.rootViewController = sideMenu
        window?.makeKeyAndVisible()

        return true
    }
```
###Installation
As for now please clone the repository and drag the source folder into your project to use SSASideMenu. (Cocoapods & Carthage
support coming soon)
###Customization
```swift

    enum SSASideMenuPanDirection: Int {
        case edge = 0
        case everyWhere = 1
    }

    enum SSASideMenuType: Int {
        case scale = 0
        case slip = 1
    }

    enum SSAStatusBarStyle: Int {
        case hidden = 0
        case black = 1
        case light = 2
    }


    struct ContentViewShadow {

        var enabled: Bool = true
        var color: UIColor = UIColor.black
        var offset: CGSize = CGSize.zero
        var opacity: Float = 0.4
        var radius: Float = 8.0

    }

    struct MenuViewEffect {

        var fade: Bool = true
        var scale: Bool = true
        var scaleBackground: Bool = true
        var parallaxEnabled: Bool = true
        var bouncesHorizontally: Bool = true
        var statusBarStyle: SSAStatusBarStyle = .black
    }

    struct ContentViewEffect {

        var alpha: Float = 1.0
        var scale: Float = 0.7
        var landscapeOffsetX: Float = 30
        var portraitOffsetX: Float = 30
        var minParallaxContentRelativeValue: Float = -25.0
        var maxParallaxContentRelativeValue: Float = 25.0
        var interactivePopGestureRecognizerEnabled: Bool = true
    }

    struct SideMenuOptions {

        var animationDuration: Float = 0.35
        var panGestureEnabled: Bool = true
        var panDirection: SSASideMenuPanDirection = .edge
        var type: SSASideMenuType = .scale
        var panMinimumOpenThreshold: UInt = 60
        var menuViewControllerTransformation: CGAffineTransform = CGAffineTransform.init(scaleX: 1.5, y: 1.5)
        var backgroundTransformation: CGAffineTransform = CGAffineTransform.init(scaleX: 1.7, y: 1.7)
        var endAllEditing: Bool = false
    }


    // MARK : Storyboard Support
    @IBInspectable var contentViewStoryboardID: String?
    @IBInspectable var leftMenuViewStoryboardID: String?
    @IBInspectable var rightMenuViewStoryboardID: String?

    // MARK : Private Properties: MenuView & BackgroundImageView
    @IBInspectable var fadeMenuView: Bool =  true
    @IBInspectable var scaleMenuView: Bool = true
    @IBInspectable var scaleBackgroundImageView: Bool = true
    @IBInspectable var parallaxEnabled: Bool = false
    @IBInspectable var bouncesHorizontally: Bool = true

    // MARK : Public Properties: MenuView
    @IBInspectable var statusBarStyle: SSAStatusBarStyle = .black

    // MARK : Private Properties: ContentView
    @IBInspectable var contentViewScaleValue: Float = 0.7
    @IBInspectable var contentViewFadeOutAlpha: Float = 1.0
    @IBInspectable var contentViewInLandscapeOffsetCenterX: Float = 30.0
    @IBInspectable var contentViewInPortraitOffsetCenterX: Float = 30.0
    @IBInspectable var parallaxContentMinimumRelativeValue: Float = -25.0
    @IBInspectable var parallaxContentMaximumRelativeValue: Float = 25.0

    // MARK : Public Properties: ContentView
    @IBInspectable var interactivePopGestureRecognizerEnabled: Bool = true
    @IBInspectable var endAllEditing: Bool = false

    // MARK : Private Properties: Shadow for ContentView
    @IBInspectable var contentViewShadowEnabled: Bool = true
    @IBInspectable var contentViewShadowColor: UIColor = UIColor.black
    @IBInspectable var contentViewShadowOffset: CGSize = CGSize.zero
    @IBInspectable var contentViewShadowOpacity: Float = 0.4
    @IBInspectable var contentViewShadowRadius: Float = 8.0

    // MARK : Public Properties: SideMenu
    @IBInspectable var animationDuration: Float = 0.35
    @IBInspectable var panGestureEnabled: Bool = true
    @IBInspectable var panDirection: SSASideMenuPanDirection = .edge
    @IBInspectable var type: SSASideMenuType = .scale
    @IBInspectable var panMinimumOpenThreshold: UInt = 60
    @IBInspectable var menuViewControllerTransformation: CGAffineTransform = CGAffineTransform(scaleX: 1.5, y:1.5)
    @IBInspectable var backgroundTransformation: CGAffineTransform = CGAffineTransform(scaleX: 1.7, y:1.7)

    // MARK : Public Properties
    weak var delegate: SSASideMenuDelegate?
    var backgroundImage: UIImage?
    var contentViewController: UIViewController?
    var leftMenuViewController: UIViewController?
    var rightMenuViewController: UIViewController?
```

###Author

Sebastian Andersen

[romaonthego/RESideMenu](https://github.com/romaonthego/RESideMenu) was
authored by Roman Efimov

###License

SSASideMenu is available under the MIT license. See the LICENSE file for more info.
