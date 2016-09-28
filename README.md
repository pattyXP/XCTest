# XCTest
# 单元测试小结


**前提**

[单元测试](https://zh.wikipedia.org/wiki/%E5%8D%95%E5%85%83%E6%B5%8B%E8%AF%95)
App由一个个功能组成，每一个功能则由相应的函数来组成，单元测试就是针对App里面的函数进行测试，有了它能使我们的项目更加的健壮，使用前提是用代码来测试所写方法，每个测试方法都是独立的.



### XCTest

XCTest就是XCode为我们提供的一个框架，它提供了各个层次的测试。
步骤：
每个XCode创建iOS的工程中都有一个叫做”工程名Tests”的分组，这个分组里就是XCTestCase的子类，XCTest中的测试类都是继承自XCTestCase。
例如新建一个工程(YYDemo)就能看到如图 

![image](http://ww4.sinaimg.cn/large/0060lm7Tgw1f89c00j2r3j31cu0wak2m.jpg)

相应的测试Target叫做'YYDemoTests'.每个测试文件都可以独立定义一个XCTest的子类，每个方法以test开头即可。使用苹果系统的assert风格，可以判断测试是不是满足某个特定的条件，不符合的话在执行的时候就会爆出Error，定位出有问题的行。


**使用**

* 测试方法的命名

  XCTest中所有的测试用例的命名都是以test开头的

* setUp

  用于在测试用例运行前，做一些初始化工作
  
* tearDown
	
  在所有的测试用例都执行完毕后执行
  
* 测试用例可以单独执行，也可以相同文件方法一起执行

* 测试的方法在控制台都会输出该方法运行的时间,如图

*  ![Image](http://ww2.sinaimg.cn/large/0060lm7Tgw1f89c55ro08j30o8092wiq.jpg)

* 举例

`

	- (void)testParseDict
	{
    //given
  
    NSDictionary *dict = [NSDictionary dictionaryWithObjectsAndKeys:@"haha",@"userName",
                          @"10",@"userAge",
                          @"China",@"country",
                          @"modelId",@"id",
                          nil];
    
    Model *model = [[Model alloc] init];
    
    //when
    [model autoParseWithDict:dict];
    
    //then
    XCTAssertNotNil(model.userName,@"parseDict Error");
	}


XCTest提供的断言有很多，可以进行值的检测：

* XCTAssertNil
* XCTAssertNotNil
* XCTAssert
* XCTAssertTrue
* XCTAssertFalse
* XCTAssertEqualObjects
* XCTAssertNotEqualObjects
* XCTAssertEqual
* XCTAssertNotEqual
* XCTAssertGreaterThan
* XCTAssertGreaterThanOrEqual
* XCTAssertLessThan
* XCTAssertLessThanOrEqual

