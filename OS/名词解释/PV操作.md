```c++
typedef struct seamphore{
	int value; //信号量值
	struct pcb *list; //信号量队列指针
};

void P(semaphore &s){
	s.value--; //占用资源
	if(s.value < 0)  //如果资源未在空闲状态
		W(s.list); // 进入等待态
}

void V(semaphore &s){
	s.value++;  //释放资源
	if(s.value <= 0) //如果有进程在等待该资源
		R(s.list); // 唤醒队首进程
}

```

