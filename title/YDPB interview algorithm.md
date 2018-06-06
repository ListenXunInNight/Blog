<H1>某跑步App公司算法面试题</H1>

>当然笔试题不只这两道，还有很多，其中最深刻的是  `weak` `strong` `copy`  `assign` `__block` `__weak` 这几个修饰符的深层考察（光这些就讲了大概有半个小时）。闲话休絮，请看正题：

<H3>1、有元素个数为n的整形数组，数组元素值范围在[1, 13]，请将数组中任意两元素相加之和为14的元素从数组中删除；<H3>

	void printArray(int *arr, int count) {
	    printf("打印所有元素\n");
	    for (int i = 0; i < count; i++) {
	        printf("%4d", arr[i]);
	    }
	    printf("\n");
	}
	
	#define kCount 10
	#define kRemoveSum 14
	
	void remove14Array() {
	    
	    /// 待剔除数据数组，需要剔除的元素的下标数组，元素值为1表示需要剔除，否则不需要
	    int number[kCount] = {0}, index[kCount] = {0};

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
	    printArray(number, kCount);
	    
		int deletedCount = 0;
		for (int i = 0, j = 0; i < kCount - deletedCount;j++) {
	        if (index[j]) deletedCount ++;
	        else {
	            /// 移除第i + deletedCount
	            number[i] = number[i + deletedCount];
	            i++;
	        }
	    }
	    printArray(number, kCount - deletedCount);
	}

<H3>2、逐层遍历二叉树；<H3>

	@interface Tree : NSObject
	@property (nonatomic, strong) Tree *left;
	@property (nonatomic, strong) Tree *right;
	@property (nonatomic, copy) NSString *node;
	@end
	
	@implementation Tree
	@end

	void boardFirstVisitTree() {
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
	

<h1><a href='../README.md'>返回列表</a> </h1>
