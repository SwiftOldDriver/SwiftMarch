# SwiftMarch
swift发展趋势喜人，github上已经有很多相关的开源项目，也有一些人进行了收集。然而我们如何判断某个开源库能否安心的在项目中使用呢？毕竟不是谁都有时间或者能力读完全部的源码，有些库即使读了源码也无法立刻得出是是否可以大规模的应用。

因此，我们决定作出一点努力。我们会筛选出**广泛应用于实际swift项目**的开源库，并且从一线开发者中搜集相关的评价。如果你打算开始一个swift项目，希望这里面的信息对你有帮助。

如果你觉得某个开源库很棒而我们遗漏了可以开PR给我们，或者对我们公布的某些库有独到的评价可以通过PR告诉我们，我们会尽快处理。

# 加入我们
这是一个完全松散的组织，加入的条件很简单：使用swift开发的优秀程序员并且愿意分享知识。我们有个QQ群，会在里面交流在swift开发遇到的各种问题。
加入方式在微博上私信发一段介绍给[冰霜 @halffrost]( http://weibo.com/u/1936502837) 或者 [@Onetaway](http://weibo.com/u/1683298872)。

# 目录

## 网络
 [Alamofire](https://github.com/Alamofire/Alamofire)

 [Moya](https://github.com/Moya/Moya)  [![GitHub stars](https://img.shields.io/github/stars/Moya/Moya.svg)]()
  * 基于Alamofire的更高层网络请求封装抽象层，Moya 本身提供了 RxSwift 扩展，可以无缝衔接 RxSwift 和 ReactiveCocoa。[Moya源码解析](http://blog.inet198.cn/?lh844386434/article/details/51818017)

## Json解析
###[SwiftyJSON](https://github.com/SwiftyJSON/SwiftyJSON)

### [ObjectMapper](https://github.com/Hearst-DD/ObjectMapper)

## 存储
[Realm](https://realm.io/cn)

## 图片存储
[Kingfisher](https://github.com/onevcat/Kingfisher)

## 布局
[SnapKit](https://github.com/SnapKit/SnapKit)

## UI
[Reusable](https://github.com/AliSoftware/Reusable)

[Spring](https://github.com/MengTo/Spring)  [![GitHub stars](https://img.shields.io/github/stars/MengTo/Spring.svg)]()
 * swift目前最常用的动画库，支持直接在storyboard添加动画。 [swift动画库spring使用和代码拆解](http://liuyanwei.jumppo.com/2015/11/22/iOS-library-spring.html)

[MaterialKit](https://github.com/nghialv/MaterialKit) [![GitHub stars](https://img.shields.io/github/stars/nghialv/MaterialKit.svg)]()
 * 将Google的UI设计语言Material Design引入到Swift中
 
## Util
###[SwiftDate](https://github.com/malcommac/SwiftDate)

###[MonkeyKing](https://github.com/nixzhu/MonkeyKing)

###[EZSwiftExtensions](https://github.com/goktugyil/EZSwiftExtensions)

###[R.swift](https://github.com/mac-cain13/R.swift)

###[PromiseKit](https://github.com/mxcl/PromiseKit) [![GitHub stars](https://img.shields.io/github/stars/mxcl/PromiseKit.svg)]()
 * Rx之外另一种异步编程的方式，模仿的就是JS的Promises，解决类似JS的回调地狱问题，代码简单易懂没有 RAC 或者 RX上手时间长的困恼。缺点可能就是没有Rx强大。[聊聊 PromiseKit
](http://swiftcafe.io/2016/07/17/promisekit/)




###[SQLite.swift](https://github.com/stephencelis/SQLite.swift) [![GitHub stars](https://img.shields.io/github/stars/stephencelis/SQLite.swift.svg)]()
 * 纯Swift版本Sqlite库,轻量，简单，好用。

###[AudioKit](https://github.com/audiokit/AudioKit) [![GitHub stars](https://img.shields.io/github/stars/audiokit/AudioKit.svg)]()
 * AudioKit是一个用于在OS X、iOS、tvOS开发中进行音频合成、处理和分析的工具集。


###[ExSwift](https://github.com/pNre/ExSwift)  [![GitHub stars](https://img.shields.io/github/stars/pNre/ExSwift.svg)]()
 * ExSwift 主要是对 Swift 中的几个基础类型进行扩展，提供了一系列非常便捷的操作。

## 加密
[CryptoSwift](https://github.com/krzyzanowskim/CryptoSwift)

## Debug
[XCGLogger](https://github.com/DaveWoodCom/XCGLogger)

[netfox](https://github.com/kasketis/netfox)   [![GitHub stars](https://img.shields.io/github/stars/kasketis/netfox.svg)]()
 * iOS/macOS网络调试的框架，这样你在开发的时候就不用charles抓包了，另外又一个好处就是不用担心发现错误而漏掉查看网络请求的历史了。实现原理很简单，利用自定义的NSURLProtocol，拦截NSURLRequest的消息，之后再转发出去。缺点就是有些NSURLSession的代理方法由于NSURLProtocol没有实现而转发不出去。
 
## 自动化
[Fastlane](https://github.com/fastlane/fastlane)

## Functional Reactive Programming
###[ReactiveCocoa](https://github.com/ReactiveCocoa/ReactiveCocoa)

###[RxSwift](https://github.com/ReactiveX/RxSwift)

## 代码分析
[SwiftLint](https://github.com/realm/SwiftLint)  [![GitHub stars](https://img.shields.io/github/stars/realm/SwiftLint.svg)]()
 * Swift代码检查及自动格式化工具,Uber现在就在使用这个库。


## Server
[Perfect](https://github.com/PerfectlySoft/Perfect) [![GitHub stars](https://img.shields.io/github/stars/PerfectlySoft/Perfect.svg)]()
 * Perfect的目标就是做成和Ruby的Rails一样

[vapor](https://github.com/vapor/vapor) [![GitHub stars](https://img.shields.io/github/stars/vapor/vapor.svg)]()
 * vapor是受PHP的 Laravel 启发

[Kitura](https://github.com/IBM-Swift/Kitura) [![GitHub stars](https://img.shields.io/github/stars/IBM-Swift/Kitura.svg)]()
 * IBM开发的服务端框架，Kitura 模仿的是node上的Web框架 Express.js 风格的框架，在语法类似vapor。

# thanks
[awesome-ios](https://github.com/vsouza/awesome-ios)



