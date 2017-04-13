# SwiftMarch
Swift 发展趋势喜人，Github 上已经有很多相关的开源项目，也有一些人进行了收集。然而我们如何判断某个开源库能否安心的在项目中使用呢？毕竟不是谁都有时间或者能力读完全部的源码，有些库即使读了源码也无法立刻得出是是否可以大规模的应用。

因此，我们决定作出一点努力。我们会筛选出**广泛应用于实际 Swift 项目**的开源库，并且从一线开发者中搜集相关的评价。如果你打算开始一个 Swift 项目，希望这里面的信息对你有帮助。

如果你觉得某个开源库很棒而我们遗漏了可以开 PR 给我们，或者对我们公布的某些库有独到的评价可以通过 PR 告诉我们，我们会尽快处理。

# 加入我们
这是一个完全松散的组织，加入的条件很简单：使用 Swift 开发的优秀程序员并且愿意分享知识。我们有个 QQ 群，会在里面交流在 Swift 开发遇到的各种问题。
加入方式在微博上私信发一段介绍给[冰霜 @halffrost]( http://weibo.com/u/1936502837) 或者 [@Onetaway](http://weibo.com/u/1683298872)。

# 目录

## 网络
### [Alamofire](https://github.com/Alamofire/Alamofire)
Swift 中使用最广泛的网络库。由大神 matt 负责，值得信赖。可以看介绍：[全身心拥抱开源的开发者 Mattt Thompson](https://github.com/ipader/SwiftGuide/wiki/全身心拥抱开源的开发者-Mattt-Thompson)。需要提醒的是 4.1.0 的版本支持 iOS 8 ， 4.0 的版本只支持 iOS 9 。

## JSON 解析
### [SwiftyJSON](https://github.com/SwiftyJSON/SwiftyJSON)
SwiftyJSON 应该算是最老牌的 JSON 解析库之一，安全快捷又不啰嗦。知道的人多，用的人多，星星也多。对于嵌套复杂的 JSON 数据依然能够如字典取值般简单；灵活地与 `if let` 配合使用，更不用担心取到了错误的数据。

### [ObjectMapper](https://github.com/Hearst-DD/ObjectMapper)
JSON 解析是 iOS 开发中再常见不过的了，也许你只听过上面星星很多的 SwiftyJSON，但是我相信你用过 ObjectMapper 后一定会喜欢上它的。首先 ObjectMapper 使用起来非常简洁，配合 [JSON Export](https://github.com/Ahmed-Ali/JSONExport) 使用，你完全不需要在嵌套的 JSON 数据里摸不着北，它还支持结构体和自定义转换。同时，ObjectMapper 还遵守面向协议编程的范式，你的 Model 只需要实现 Mappable 协议就可以了，这会让你的代码更 Swifty。如果你想让你的 Model 看起来既优雅又清爽，那么我建议你一定要试一试这个库。

这是 ObjectMapper 的[中文文档翻译]( https://github.com/lacklock/ObjectMapper-CN-Guide)。

## 存储
### [YYCache](https://github.com/ibireme/YYCache)

轻量级缓存的最可靠选择。不得不承认的一个事实是目前没有一个用 Swift 编写的优秀缓存库。最流行的 Haneke 作者在 2.3 版本后已经放弃维护，当然本身 Haneke 的实现也不算优秀。虽然 OC 中的基本数据对象在 Swift 中使用需要经过类型转换，但是经过实际测试这部分性能损失在日常业务处理中并没有多大的影响，属于可以接受的范围。

具体设计介绍参考作者写的：[YYCache 设计思路与技术细节](http://blog.ibireme.com/2015/10/26/yycache/)。

### [Realm](https://realm.io/cn)  
Realm 是由硅谷创业公司发布的一款可以用于 iOS 和 Android 的跨平台移动数据库。支持的平台包括 Java，Objective-C，Swift，React Native，Xamarin。是第一个专门针对移动平台的数据库，立志取代 SQLite 、CoreData。核心数据引擎由 C++ 开发，有着优异的性能。简单易用可以快速上手，在数据存储时再也不用思考烦人的底层技术细节。

基于技术选型的限制，目前 Realm 使用中也有一些明显的不便：
-  Realm 没有自动增长属性

    Realm 没有线程/进程安全的自动增长属性机制，这在其他数据库中常常用来产生主键

-  所有的数据模型必须直接继承自 RealmObject 。这阻碍我们利用数据模型中的任意类型的继承。以下是不能完成的：  

   - 多态类之间的转换（例如子类转换成子类，子类转换成父类，父类转换成子类等）
   - 同时对多个类进行检索
   - 多类容器 (RLMArray 以及 RLMResults)  

-  NSData 以及 NSString 属性不能保存超过 16 MB 大小的数据

-  不能自定义 getter、setter

     realm会自动生成 getter、setter ，如果自定义 getter 、setter 存储就会有影响。如果要规避这个问题，可以通过设置这个对象的忽略属性。

-  查询的结果不是数组

     为了能够支持查询结果的链式查询，realm 自定义了一个集合类型。可以枚举，但是不是熟悉的数组了。又因为realm的懒加载机制，所以不建议在数据层把这个枚举转成数组类型。这样的缺点就是上层知道了数据的存储逻辑。严格的说这里不应该让上层知道。但是这样设计也许是为了方便上层进行再次检索，realm有着优越的查询性能。

-  尽管 Realm 文件可以被多个线程同时访问，但是您不能跨线程处理 Realms、Realm 对象、查询和查询结果

-  Realm不能支持原生的集合类型，比如：NSArray 、NSDictionary 、NSSet 等。需要使用 Realm 里面提供的集合类型 RLMArray(OC)，List(Swift)



关于 Realm 的基本情况介绍，可以看这篇文章：[移动端数据库新王者：realm](http://www.jianshu.com/p/2b4388cf2a2d)。   

**关于 Realm 的详细使用**，可以查看[官方文档](https://realm.io/docs/swift/latest/)。

更多的具体分析，请前往[Realm数据库 从入门到“放弃”](http://www.jianshu.com/p/50e0efb66bdf)。

## 图片存储
### [Kingfisher](https://github.com/onevcat/Kingfisher)  
Kingfisher 是 Swift 中使用比较广泛的图片存储库。由喵神 onevcat 开源及维护。 Kingfisher 轻量级，纯 Swift 编写，目的是为了解决从网络上下载图片和缓存图片的问题。Kingfisher 的灵感主要来源于 SDWebImage，采用的存储机制和 SDWebImage一样，所以性能上没有太大区别，然而却有着更加灵活友好的 API。

目前支持 iOS 8.0+ / macOS 10.10+ / tvOS 9.0+ / watchOS 2.0+，Swift 3 (Kingfisher 3.x), Swift 2.3 (Kingfisher 2.x)。

关于 Kingfisher 的使用，详细请看这篇[文档](https://github.com/onevcat/Kingfisher/wiki)。

## 布局
### [SnapKit](https://github.com/SnapKit/SnapKit)
如果你使用 Autolayout 布局，Snapkit 就是最好的第三方库。完整的提供了底层的能力。创造性的引入链式编程，让使用起来非常的方便。

## UI
### [Reusable](https://github.com/AliSoftware/Reusable)
UITableView 必备。更加优雅的实现 Cell 的 Register 和 Reuse 。使用参考：[Reusable-让你放肆的dequeueReusableCell](http://www.jianshu.com/p/255e02337176)。

## Util
### [SwiftDate](https://github.com/malcommac/SwiftDate)
非常好用的帮助处理 Date 相关的库。灵活运用了 swift 的重载操作符、扩展等特性，使得时间可以直观的进行算术运算：比较大小，直接加减等。常见的时间也字符串的转换也做了良好的支持。

### [MonkeyKing](https://github.com/nixzhu/MonkeyKing)
MonkeyKing 帮助开发者快速集成国内主流社交应用(微信、微博、QQ、支付宝)的分享、授权、支付等功能。重要的是，不需要集成各种官方 SDK。目前由 4 名程序员维护。可用于生产环境、轻量级，能满足绝大部分的分享、授权、支付等需求。


###[EZSwiftExtensions](https://github.com/goktugyil/EZSwiftExtensions)
提供了一系列对于 Swift 标准库、方法与 UIKit 的扩展，让你更加简单舒服地编写代码。


###[R.swift](https://github.com/mac-cain13/R.swift)
配置稍微有一点复杂，然而付出的努力对于项目而言是值得的。R.swfit 会根据项目文件在编译期生成各种资源文件的枚举，比如 nib 、UIImage 等。大幅度减少了使用资源文件时输入字符串的这种痛苦。有一个缺点就是这个库只适合使用在纯 Swift 项目中。可以参考：[R.swift:以一种优雅安全的方式使用资源文件](http://www.jianshu.com/p/b453b78c7126)。


###[SwiftyAttributes](https://github.com/eddiekaiger/SwiftyAttributes)
先进的 API ，操作 attributed 字符串的利器。


## 加密
###[CryptoSwift](https://github.com/krzyzanowskim/CryptoSwift)
非常流行的加密解密库，项目配有完善的单元测试，可以放心使用。

###[KeychainAccess](https://github.com/kishikawakatsumi/KeychainAccess)
轻量级 Keychain 封装,简单到极致的接口。支持 TouchID 与 Keychain 整合，详细、优雅、简明的 README。Objective-C 版本在[这里](https://github.com/soffes/SAMKeychain)


## Debug
###[XCGLogger](https://github.com/DaveWoodCom/XCGLogger)
由于 Swift 本身不包含 C 的预编译器，导致开发者不能使用在 OC 中定义过的宏定义进行调试打印。简单的打印调用栈的信息，又会漏掉很多有用信息。想要解决这个问题又需要加入更多的代码。基于这个目的， XCGLogger 给纯的 Swift 项目带来了解决方案。 XCGLogger 允许你在控制台记录任何细节，使用起来极其简单，和使用 nslog() 或 print() 一样方便。 XCGLogger 可以打印任何信息，甚至可以打印日期、函数名、文件名和行号等等。

###[CocoaLumberjack](https://github.com/CocoaLumberjack/CocoaLumberjack)
OC 时代最好用的记录日志的开源库。现在同时有 OC 版和 swift 版本提供。

## 自动化
###[Fastlane](https://github.com/fastlane/fastlane)
iOS 中最好用的自动化工具。提供了获取证书、运行自动化测试、上传至 TestFlight 和 AppStore 等功能。配置简单，社区强大，具体的功能可以到这个网站查看：[fastlane.tools](https://fastlane.tools/)。

## Functional Reactive Programming
使用响应式编程框架统一对委托、回调 blocks 、通知 、控件的事件 、KVO 等异步事件的逻辑处理。可以显著的降低代码复杂度，更有效的传达代码意图。任何一个优秀的 iOS 程序员都不会拒绝响应式编程，唯一的缺点可能就是对智商有要求了。

RAC 和 Rx 都有着广泛的使用用户。个人拙见两个库的选择全靠个人偏好，在编程范式上没有区别。

###[ReactiveCocoa](https://github.com/ReactiveCocoa/ReactiveCocoa)
OC 时代最流行的响应式框架。由 github 团队开源。如果项目是从 OC 迁移到 swift 的，继续使用 RAC 是一个非常自然的选择。因此 RAC 有着广泛的社区支持。从  5.0 开始主要框架逻辑已经全由 swift 实现。与 RxSwift 编程模型最大的区别是冷热信号由两种类型表示。

###[RxSwift](https://github.com/ReactiveX/RxSwift)
函数响应式编程 (Funtional Reactive Programming) 系列 ReactiveX 的 Swift 版本开源框架。推出时间较晚，其思路与 ReactiveCocoa 相近，它们的共同祖先是微软的 ReactiveExtensions，本质核心就是面向数据流编程。

## 代码分析
###[SwiftLint](https://github.com/realm/SwiftLint)
Realm 出品的 Swift 代码规范检测工具。深度嵌入 Clang 和 SourceKit，可以监测整个项目的代码风格。如果有不符合规范之处，SwiftLint会报出相应警告⚠️。当然为了方便和特殊情况，也可在相应代码处手动关闭警告，或是在整个项目中关闭警告，十分灵活。

代码规范请参考：[Swift Style Guide](https://github.com/Artwalk/swift-style-guide/blob/master/README_CN.md)

# Thanks
[awesome-ios](https://github.com/vsouza/awesome-ios)



