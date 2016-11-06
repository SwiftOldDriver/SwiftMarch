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
Swift 中使用最广泛的网络库。由大神 matt 负责，值得信赖。可以看介绍：[全身心拥抱开源的开发者 Mattt Thompson](https://github.com/ipader/SwiftGuide/wiki/全身心拥抱开源的开发者-Mattt-Thompson)。稍微有点遗憾的是官方的 Swift 3.0 版本响应苹果的号召并不支持 iOS 8。只有 2.3 的版本才支持 iOS 8。

## JSON 解析
### [SwiftyJSON](https://github.com/SwiftyJSON/SwiftyJSON)

### [ObjectMapper](https://github.com/Hearst-DD/ObjectMapper)

## 存储
### [Realm](https://realm.io/cn)  
Realm 是由硅谷 Realm 团队开源的数据库。Realm 不基于 ORM，也不基于 SQLite 创建，而是为移动开发者定制的全功能数据库。它可以将原生对象直接映射到Realm的数据库引擎（远不仅是一个键值对存储）中。 Realm 是一个 MVCC 数据库 ，数据库底层由 C++ 编写而成。 
Realm 满足 ACID 模型。原子性（Atomicity）、一致性（Consistency）、隔离性（Isolation）、持久性（Durability），一个支持事务（Transaction）的数据库，必需要具有这四种特性。Realm 都已经全部满足。

**关于 Realm 的碾压级的性能**，可以看这篇文章的介绍[移动端数据库新王者：realm](http://www.jianshu.com/p/2b4388cf2a2d)。   
**关于 Realm 的详细使用**，可以查看[官方文档](https://realm.io/docs/swift/latest/)。

虽说 Realm 的性能很强，但是目前最新版本依旧有一些限制，需要你考虑，这将是决定你是否能优雅的切换到 Realm 数据库的关键。目前最新版本是 2.0.3，有以下的一些限制： 

1. 类名称的长度最大只能存储 57 个 UTF8 字符。

2. 属性名称的长度最大只能支持 63 个 UTF8 字符。

3. NSData 以及 NSString 属性不能保存超过 16 MB 大小的数据。

4. 对字符串进行排序以及不区分大小写查询只支持“基础拉丁字符集”、“拉丁字符补充集”、“拉丁文扩展字符集 A” 以及”拉丁文扩展字符集 B“（UTF-8 的范围在 0~591 之间）。

5. 尽管 Realm 文件可以被多个线程同时访问，但是您不能跨线程处理 Realms、Realm 对象、查询和查询结果。

6. Realm 对象的 Setters & Getters 不能被重载

7. 文件大小 & 版本跟踪

 如果您从 Realm 读取了一些数据并进行了在一个锁定的线程中进行长时间的运行，然后在其他线程进行读写 Realm 数据库的话，那么版本将不会被更新，Realm 将保存中间版本的数据，但是这些数据已经没有用了，这导致了文件大小的增长。这部分空间会在下次写入操作时被重复利用。这些操作可以通过调用`-writeCopyToPath:error:`来实现。

8. Realm 没有自动增长属性

 Realm 没有线程/进程安全的自动增长属性机制，这在其他数据库中常常用来产生主键。

9. Realm不能支持原生的集合类型，比如NSArray，NSMutableArray，NSDictionary，NSMutableDictionary,NSSet,NSMutableSet。但是可以使用 Realm 里面给的集合类型 RLMArray(OC)，List(Swift)。

10. 所有的数据模型必须直接继承自 RealmObject。这阻碍我们利用数据模型中的任意类型的继承。以下是不能完成的：  

- 多态类之间的转换（例如子类转换成子类，子类转换成父类，父类转换成子类等）

- 同时对多个类进行检索

- 多类容器 (RLMArray 以及 RLMResults)  



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

### [MonkeyKing](https://github.com/nixzhu/MonkeyKing)
MonkeyKing 帮助开发者快速集成国内主流社交应用(微信、微博、QQ、支付宝)的分享、授权、支付等功能。重要的是，不需要集成各种官方 SDK。目前由 4 名程序员维护。可用于生产环境、轻量级，能满足绝大部分的分享、授权、支付等需求。

###[EZSwiftExtensions](https://github.com/goktugyil/EZSwiftExtensions)
提供了一系列对于 Swift 标准库、方法与 UIKit 的扩展，让你更加简单舒服地编写代码。

###[R.swift](https://github.com/mac-cain13/R.swift)
配置稍微有一点复杂，然而付出的努力对于项目而言是值得的。R.swfit 会根据项目文件在编译期生成各种资源文件的枚举，比如 nib 、UIImage 等。大幅度减少了使用资源文件时输入字符串的这种痛苦。有一个缺点就是这个库只适合使用在纯 Swift 项目中。可以参考：[R.swift:以一种优雅安全的方式使用资源文件](http://www.jianshu.com/p/b453b78c7126)。

## 加密
###[CryptoSwift](https://github.com/krzyzanowskim/CryptoSwift)
非常流行的加密解密库，项目配有完善的单元测试，可以放心使用。

## Debug
###[XCGLogger](https://github.com/DaveWoodCom/XCGLogger)

###[CocoaLumberjack](https://github.com/CocoaLumberjack/CocoaLumberjack)
OC 时代最好用的记录日志的开源库。现在同时有 OC 版和 swift 版本提供。

## 自动化
###[Fastlane](https://github.com/fastlane/fastlane)
iOS 中最好用的自动化工具。提供了获取证书、运行自动化测试、上传至 TestFlight 和 AppStore 等功能。配置简单，社区强大，具体的功能可以到这个网站查看：[fastlane.tools](https://fastlane.tools/)。

## Functional Reactive Programming
###[ReactiveCocoa](https://github.com/ReactiveCocoa/ReactiveCocoa)

###[RxSwift](https://github.com/ReactiveX/RxSwift)

## 代码分析
###[SwiftLint](https://github.com/realm/SwiftLint)

# Thanks
[awesome-ios](https://github.com/vsouza/awesome-ios)



