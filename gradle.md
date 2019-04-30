
[Gradle 提示与诀窍](https://developer.android.com/studio/build/gradle-tips?hl=zh_cn)
[Gradle](https://gradle.org/?hl=zh_cn)

 


#### `dependencies` 参数含义
- ###### `compile`（api）
  这种是我们最常用的方式，使用该方式依赖的库将会参与编译和打包。

- ###### `provided`（compileOnly）
  只在编译时有效，不会参与打包，可以在自己的moudle中使用该方式依赖。比如com.android.support，gson这些使用者常用的库，避免冲突。 
- ###### `apk`（runtimeOnly）
  只在生成apk的时候参与打包，编译时不会参与，很少用。

- ###### `testCompile`（testImplementation）
  testCompile 只在单元测试代码的编译以及最终打包测试apk时有效。

- ###### `debugCompile`（debugImplementation）
  debugCompile 只在debug模式的编译和最终的debug apk打包时有效。

- ###### `releaseCompile`（releaseImplementation） 
  releaseCompile 仅仅针对Release模式的编译和最终的Release apk打包。

#### Gradle [构建流程](https://developer.android.com/studio/build/index.html?hl=zh_cn)
![构建流程](https://developer.android.com/images/tools/studio/build-process_2x.png?hl=zh_cn "dd")

#### [添加构建依赖项](https://developer.android.com/studio/build/dependencies?hl=zh_cn)

|  新配置|已弃用配置|行为|
| ------------ | ------------ |------------|
|  implementation | compile  |Gradle 会将依赖项添加到编译类路径，并将依赖项打包到构建输出。但是，当您的模块配置 implementation 依赖项时，会告知 Gradle 您不想模块在编译时将依赖项泄露给其他模块。也就是说，依赖项只能在运行时供其他模块使用。<br>使用此依赖项配置而不是 api 或 compile（已弃用），可以显著缩短构建时间，因为它可以减少构建系统需要重新编译的模块数量。例如，如果 implementation 依赖项更改了其 API，Gradle 只会重新编译该依赖项和直接依赖它的模块。大多数应用和测试模块都应使用此配置
| api  | compile  |Gradle 会将依赖项添加到编译类路径，并构建输出。当模块包括 api 依赖项时，会告知 Gradle 模块想将该依赖项间接导出至其他模块，以使这些模块在运行时和编译时均可使用该依赖项。<br>此配置的行为类似于 compile （现已弃用），但您应仅对需要间接导出至其他上游消费者的依赖项慎重使用它。 这是因为，如果 api 依赖项更改了其外部 API，Gradle 会重新编译可以在编译时访问该依赖项的所有模块。 因此，拥有大量 api 依赖项会显著增加构建时间。 如果不想向不同的模块公开依赖项的 API，库模块应改用 implementation 依赖项。|
|  compileOnly | provided  | Gradle 只会将依赖项添加到编译类路径（即不会将其添加到构建输出）。如果是创建 Android 模块且在编译期间需要使用该依赖项，在运行时可选择呈现该依赖项，则此配置会很有用。<br> 如果使用此配置，则您的库模块必须包含运行时条件，以便检查是否提供该依赖项，然后妥善更改其行为，以便模块在未提供依赖项的情况下仍可正常工作。这样做不会添加不重要的瞬时依赖项，有助于缩减最终 APK 的大小。 此配置的行为类似于 provided （现已弃用）。 |
|  runtimeOnly | apk  | Gradle 只会将依赖项添加到构建输出，供运行时使用。也就是说，不会将其添加到编译类路径。 此配置的行为类似于 apk（现已弃用）。  |
|annotationProcessor|compile|要在库中添加注解处理器依赖项，则必须使用 annotationProcessor 配置将其添加到注解处理器类路径。这是因为使用此配置可分离编译类路径与注解处理器类路径，从而提升构建性能。如果 Gradle 在编译类路径上找到注解处理器，则会停用 避免编译功能，这样会增加构建时间（Gradle 5.0 和更高版本会忽略编译类路径上的注解处理器）。<br>如果 JAR 文件包含以下文件，则 Android Gradle Plugin 会假定依赖项是注解处理器：META-INF/services/javax.annotation.processing.Processor。 如果插件检测到编译类路径上包含注解处理器，则会生成构建错误。|

