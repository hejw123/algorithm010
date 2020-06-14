##  斐波那契数列
int first = 1;  // 第一个值
int second = 2; // 第二个值
int third = 0;  // 第三个值
// 包括第n个
for( int i = 1 ; i <= n ; i++ ) {
	if ( i == 1 ) {
		third = first;
	} else if ( i == 2 ) {
		third = second ;
	} else {
		// 循环覆盖前面两个值
		third  = first + second ;
		first  = second;
		second = third;
	}
}
return second
