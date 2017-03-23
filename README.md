# Objective-C-nil-Nil-NULL-NSNull-
Objective-C中nil, Nil, NULL和NSNull的区别
区别

Symbol	Value	Meaning
NULL	(void *)0	literal null value for C pointers
nil	(id)0	literal null value for Objective-C objects
Nil	(Class)0	literal null value for Objective-C classes
NSNull	[NSNull null]	singleton object used to represent null
## 1. nil：对象为空

定义某一实例对象为空值。例如：
```objc
NSObject* obj = nil;  
if (nil == obj) {  
    NSLog(@"obj is nil");  
}  
else {  
    NSLog(@"obj is not nil");  
}
```
## 2. Nil：类为空

定义某一类为空。例如:
```
Class someClass = Nil;  
Class anotherClass = [NSString class];
```
## 3. NULL：基本数据对象指针为空

NULL是无类型的，只是一个宏，它代表为空。用于c语言的各种数据类型的指针为空。例如：
```
intint *pointerToInt = NULL;   
charchar *pointerToChar = NULL;   
struct TreeNode *rootNode = NULL;
```
## 4. NSNull

集合对象无法包含 nil 作为其具体值，如NSArray、NSSet和NSDictionary。相应地，nil值用一个特定的对象 NSNull 来表示。NSNull 提供了一个单一实例用于表示集合对象属性中的的nil值。
```objc
@interface NSNull : NSObject <NSCopying, NSSecureCoding>  
+ (NSNull *)null;
@end
```
在NSNull单例类中，提供了唯一的方法null：Returns the singleton instance of NSNull.
例如：
```
NSMutableDictionary *mutableDictionary = [NSMutableDictionary dictionary];  
mutableDictionary[@"someKey"] = [NSNull null]; // Sets value of NSNull singleton for `someKey`  
NSLog(@"Keys: %@", [mutableDictionary allKeys]); // @[@"someKey"]
```
