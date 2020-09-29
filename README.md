int main()
{
	int arr[] = {1,2,3,4,5};
	short* p = (short *)arr;
	int i;
	int sz = sizeof(arr) / sizeof(arr[0]);
	for (i = 0; i < 6; i++)
	{

		*(p + i) = 0;//相当于*p++ = 0; short类型两个两个字节跳


	}

	for (i = 0; i < 6; i++)
	{
		printf("%d  ",arr[i]);
	}

}
//这是一个关于init数组的代码，运行结果：0,0,0,4,5
//请观察下面的代码：
int main()
{
	int arr[] = {1,2,3,4,5};
	short* p = (short *)arr;
	int i;
	int sz = sizeof(arr) / sizeof(arr[0]);
	for (i = 0; i < 6; i++)
	{

		*(p + i) = 0;//相当于*p++ = 0; short类型两个两个字节跳
		printf("%d  ", arr[i]);

	}
	/*
	for (i = 0; i < 6; i++)
	{
		printf("%d  ",arr[i]);
	}
	*/
}
/*
大家想想结果？
是不是感觉是一样的。
结果当然不是！
运行结果为 0,2,3,4,5
为何？
在visual 2019中调试观察前后地址得出答案，因为在for内i的值与p移动变化的有所不同，p要加上2才能看到结果，而i则是直接输出还没移动过去的值
结论：
所以把在不同类型变量（转换）过程中，把输出语句放在P自增的for，是不安全的，编程是需要注意
*/ 
