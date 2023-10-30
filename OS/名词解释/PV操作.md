```c++

//此部分为源语操作，一个函数要么不进行，要么一次性进行完全，不会出现竞争
typedef struct seamphore{
	int value; //信号量值
	struct pcb *list; //信号量队列指针
};

void P(semaphore &s){
	s.value--;  //申请资源
	if(s.value < 0)
		W(s.list); // 进入等待态
}

void V(semaphore &s){
	s.value++;  //释放资源
	if(s.value <= 0)
		R(s.list);
}

```

```
互斥关系：
seamphore s = 1;

p1(){
	...
	P(s);
	//临界区
	V(s);
};
p2(){
	...
	P(s);
	//临界区
	V(s);
}
```

```c++
协同关系
seamphore s1 = 1, s2 = 0;//控制谁先做谁后作

p1(){
	P(s1);   //先做
	//临界区
	V(s2);
}
p2(){
	P(s2);    //p1做完才能做
	//临界区
	V(s1);
}
```

^63bc8f
