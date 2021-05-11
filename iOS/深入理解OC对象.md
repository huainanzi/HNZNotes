> 理解一个OC对象的本质，内存布局。有助于在在开发中分析和理解问题的本质，快速定位问题。

# OC对象的本质

一个OC对象经过编译后，最终都会转换成C/C++的结构体。通过**xcrun -sdk iphoneos clang -arch arm64 -rewrite-objc OC源文件 -o xx.cpp**这个命令得的转化后的cpp代码。用简单的创建NSObject对象尝试:

```objective-c
int main(int argc, const char * argv[]) {
    @autoreleasepool {
        NSObject *objc = [[NSObject alloc] init];
    }
    return 0;
}
```

转化后,在编译后的cpp代码中找到NSObjct的结构体实现，可以看出NSObject的结构体中只包含了一个**isa**指针成员

```objective-c
struct NSObject_IMPL {
	Class isa;
};
```

将情况稍复杂些。创建一个继承NSObject的HNZCar:



# NSObject的内存布局

