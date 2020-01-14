# Flutter : flutter build app 报错
Android dependency 'androidx.core:core' has different version for the compile (1.0.0-rc01) and runtime (1.0.2) classpath.

具体如下：

```
* What went wrong:                                                                                                 
Execution failed for task ':app:preReleaseBuild'.                                                                  
> Android dependency 'androidx.core:core' has different version for the compile (1.0.0-rc01) and runtime (1.0.2) classpath. You should manually set the same version via DependencyResolution
```

经过搜索找到解决办法如下：

build.gradle中添加如下内容：

```
subprojects {
        project.configurations.all {
            resolutionStrategy.eachDependency { details ->
                if (details.requested.group == 'com.android.support'
                        && !details.requested.name.contains('multidex') ) {
                    details.useVersion "27.1.1"
                }

                if (details.requested.group == 'androidx.core'
                        && !details.requested.name.contains('androidx') ) {
                    details.useVersion "1.0.1"
                }
            }
        }
    }

```

添加前：

```
buildscript {
    ext.kotlin_version = ‘1.2.71’
    repositories {
        google()
        jcenter()
    }

    dependencies {
        classpath ‘com.android.tools.build:gradle:3.2.1'
        classpath "org.jetbrains.kotlin:kotlin-gradle-plugin:$kotlin_version"
    }
}

```

添加后：

```
buildscript {
    ext.kotlin_version = ‘1.3.0’
    repositories {
        google()
        jcenter()
    }

    dependencies {
        classpath 'com.android.tools.build:gradle:3.3.1'
        classpath "org.jetbrains.kotlin:kotlin-gradle-plugin:$kotlin_version"
    }
		
		subprojects {
        project.configurations.all {
            resolutionStrategy.eachDependency { details ->
                if (details.requested.group == 'com.android.support'
                        && !details.requested.name.contains('multidex') ) {
                    details.useVersion "27.1.1"
                }

                if (details.requested.group == 'androidx.core'
                        && !details.requested.name.contains('androidx') ) {
                    details.useVersion “1.0.2"
                }
            }
        }
    }
}

```

后来发现是gradle版本和kotlin_version的问题，还是build.gradle文件：

改之前：

```
buildscript {
    ext.kotlin_version = ‘1.2.71’
    repositories {
        google()
        jcenter()
    }

    dependencies {
        classpath ‘com.android.tools.build:gradle:3.2.1'
        classpath "org.jetbrains.kotlin:kotlin-gradle-plugin:$kotlin_version"
    }
}

```

改之后：

```
buildscript {
    ext.kotlin_version = ‘1.3.0’
    repositories {
        google()
        jcenter()
    }

    dependencies {
        classpath 'com.android.tools.build:gradle:3.3.1'
        classpath "org.jetbrains.kotlin:kotlin-gradle-plugin:$kotlin_version"
    }
}

```

成功打包！！！