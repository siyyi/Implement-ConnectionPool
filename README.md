# siyyi-Implement-ConnectionPool
1、连接池只需要一个实例，采用懒汉式单例模式设计，以此来保证线程安全
2、connectionPool可以获取mysql连接
3、连接池以队列形式维护，由于对队列生产/消费连接的操作不是线程安全的，所以对其加了互斥锁unique_lock
4、使用智能指针shared_ptr管理用户连接，通过lambda表达式自定义连接释放功能（将连接重新放回连接池，而不是析构掉）
5、使用线程间同步通信机制
