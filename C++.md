 1. memset 原理
	1. 为什么memset只能初始化0和-1？
	2. 为什么程序1中的第一个memset不能使每个数组值都初始化为0？只能初始化前三个。而后面两个memset却可以？
	3. 程序2即为根据源码而来的memset实现（速度上和库函数中的memset要慢很多）
	4. memset是按字节（char）进行初始化，int是4个字节，memset把每个字节都赋值，也就是说，比如memset（a,2,sizeof(a))  则00000010 00000010 00000010 00000010
		而0，则是00000000 00000000 00000000 00000000结果是0
		而-1，则是11111111 11111111 11111111 11111111结果也是-1
		所以只能初始化0和-1；
	5. count 应为数组dst所占的字节的个数，而不是在数组dst的大小，所以count = 10只能初始化数组中的前10个字节，表现为初始化了数组中的前3个数。
    ```cpp
    // 程序1
    int dp[10] = {1, 2, 3, 4, 5, 6, 7, 8, 9, 10};
    memset(dp, 0, 10);
    memset(dp, 0, sizeof(dp));
    memset(dp, 0, 10 * sizeof(int));
    // 程序2
    void* memset2(void* dst,int val, size_t count)
    {
        void* ret = dst;
        while(count--)
        {
            *(char*)dst = (char)val;
            dst = (char*)dst + 1;
        }
        return ret;
    }
    ``` 
