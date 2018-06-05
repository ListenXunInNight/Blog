
<h1><a href='../README.md'>返回列表</a> </h1>

#某跑步App公司算法面试题

1、有元素个数为n的整形数组，数组元素值范围在[1, 13]，请将数组中任意两元素相加之和为14的元素从数组中删除；

2、逐层遍历二叉树；

以下为代码实现：

	/**
	 根据索引将某个元素从数组中移除
	
	 @param arr 数组
	 @param count 元素数量
	 @param index 下标
	 */
	void arrayRemoveElementAtIndex(int *arr, int count, int index) {
	    
	    if (index >= count) return;
	    
	    for (int i = index; i < count - 1; i++) {
	        arr[i] = arr[i + 1];
	    }
	}
	
	void printArray(int *arr, int count) {
	    printf("打印所有元素\n");
	    for (int i = 0; i < count; i++) {
	        printf("%4d", arr[i]);
	    }
	    printf("\n");
	}
	
	@interface Tree : NSObject
	@property (nonatomic, strong) Tree *left;
	@property (nonatomic, strong) Tree *right;
	@property (nonatomic, copy) NSString *node;
	@end
	
	@implementation Tree
	@end

	@implementation XxxInterview

	+ (void)remove14Array {
    
	#define kCount 10
	#define kRemoveSum 14
	    
	    /// 待剔除数据数组，需要剔除的元素的下标数组，元素值为1表示需要剔除，否则不需要
	    int number[kCount] = {0}, index[kCount] = {0};
	    int count = kCount;
	    /// 赋值
	    for (int i = 0; i < kCount; i++) {
	        number[i] = 1 + arc4random() % 13;
	        if (number[i] == 4) {
	            /// 测试保证10不会被删除
	            number[i] = 5;
	        }
	    }
	    
	    for (int i = 0; i < kCount; i++) {
	        for (int j = i + 1; j < kCount; j++) {
	            if (number[i] + number[j] == kRemoveSum) {
	                
	                index[i] = 1;
	                index[j] = 1;
	            }
	        }
	    }
	    printArray(number, count);
	    /// 从后往前删，防止下标错乱
	    for (int i = kCount - 1; i >= 0; i--) {
	        if (index[i]) {
	            arrayRemoveElementAtIndex(number, count, i);
	            count --;
	        }
	    }
	    printArray(number, count);
	}

	+ (void)boardFirstVisitTree {
	    /// 将树子节点保存至队列中，每次访问队首；并将队首的左右节点添加至队尾
	    Tree *tree = [[Tree alloc] init];
	    NSMutableArray <Tree *> *queue = @[tree].mutableCopy;
	    
	    while (queue.count) {
	        if (queue.firstObject.left) [queue addObject:queue.firstObject.left];
	        if (queue.firstObject.right) [queue addObject:queue.firstObject.right];
	        NSLog(@"%@", queue.firstObject);
	        [queue removeObjectAtIndex:0];
	    }
	}
	
	@end
