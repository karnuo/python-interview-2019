## Python开发工程师笔试题

> 答题要求：将该项目从[地址1](<https://github.com/jackfrued/python-interview-2019>)或[地址2](<https://gitee.com/jackfrued/python-interview-2019>)fork到自己的[github]()或[gitee]()仓库并填写答案，完成之后将自己的仓库（public）地址发给面试官即可，答题时间120分钟。

1. 下面的Python代码会输出什么。

   ```Python
   print([(x, y) for x, y in zip('abcd', (1, 2, 3, 4, 5))])
   print({x: f'item{x ** 2}' for x in range(5) if x % 2})
   print(len({x for x in 'hello world' if x not in 'abcdefg'}))
   ```

   答案：

   ```
   [(a,1),(b,2),(c,3),(d,4)]
   {1:'item1',3:'item9',5:'item25'}
   6
   ```

2. 下面的Python代码会输出什么。

   ```Python
   from functools import reduce
   
   items = [11, 12, 13, 14] 
   print(reduce(int.__mul__, map(lambda x: x // 2, filter(lambda x: x ** 2 > 150, items))))
   ```

   答案：

   ```
   42
   ```

3. 有一个通过网络获取数据的Python函数（可能会因为网络或其他原因出现异常），写一个装饰器让这个函数在出现异常时可以重新执行，但尝试重新执行的次数不得超过指定的最大次数。

   答案：

   ```Python
   from functools import wraps
   
   
   def outter(func):
   
       @wraps(func)
       def inner(*args,**kwargs):
           for i in range(maxcount):
               try:
                   result = func(*args,**kwargs)
                   break
               except:
                   continue
           return result
       return inner
   
   @outter
   def get_data(*args,**kwargs):
       pass
   ```

4. 下面的字典中保存了某些公司今日的股票代码及价格，用一句Python代码从中找出价格最高的股票对应的股票代码，用一句Python代码创建股票价格大于100的股票组成的新字典。

   > 说明：美股的股票代码是指英文字母代码，如：AAPL、GOOG。

   ```Python
   prices = {
       'AAPL': 191.88,
       'GOOG': 1186.96,
       'IBM': 149.24,
       'ORCL': 48.44,
       'ACN': 166.89,
       'FB': 208.09,
       'SYMC': 21.29
   }
   ```

   答案：

   ```Python
   max(prices,key=lambda x : prices[x])
   dict(sorted(filter(lambda x: items[x] > 150, items), key=lambda item:item[1]))
   ```

5. 用生成式实现矩阵的转置操作。例如，用`[[1, 2], [3, 4], [5, 6]`表示矩阵$\begin{bmatrix}1 & 2\\\\3 &4\\\\5 & 6\end{bmatrix}$，写一个生成式将其转换成`[[1, 3, 5], [2, 4, 6]]`即$\begin{bmatrix}1 & 3 & 5\\\\2 & 4 & 6\end{bmatrix}$。

   答案：

   ```Python
   [].append([item[0]for item in items ])
   ```

6. 写一个函数，传入的参数是一个列表（列表中的元素可能也是一个列表），返回该列表最大的嵌套深度，例如：

   > 参数：`[1, 2, 3]`
   >
   > 返回：`1`
   >
   > 参数：`[[1], [2, [3]]]`
   >
   > 返回：`3`

   答案：

   ```Python
   def len_list(list1:list):
       i = 0
       while True:
           list2 = []
           i += 1
           for item in list1:
               if isinstance(item,list):
                   list2.extend(item)
           if len(list2) == 0:
               break
           list1 = list2
        return i
   ```

7. 写一个函数，实现将输入的长链接转换成短链接，每个长链接对应的短链接必须是独一无二的且每个长链接只应该对应到一个短链接，假设短链接统一以`http://t.cn/`开头。

   > 参数：`http://jackfrued.xyz/api/users/10001`
   >
   > 返回：`http://t.cn/E6MUth1`

   答案：

   ```Python
   
   ```

8. 用5个线程，将1~100的整数累加到一个初始值为0的变量上，每次累加时将线程ID和本次累加后的结果打印出来。

    答案：

    ```Python
    from threading import Thread,Lock
    
    i = 0 
    lock = Lock()
    def add_num():
        for x in range(100):
            lock.acquire()
            i += x
            print(current_threading,i)
            lock.realease()
    
    def main():
        thread_pool = [Thread(target=add_num,) for _ in range(5)] 
        for thread in thread_pool:
            thread.run()
        for thread in thread_pool:
            thread.join()
      
    if __name__ == '__main__':
        main()
        
    ```

9. 请阐述Python是如何进行内存管理的。

    答案：

    ```
    python垃圾回收机制通过引用计数
    
    
    ```

10. 在MySQL数据库中有名为`tb_result`的表如下所示，请写出能查询出如下所示结果的SQL。

  `tb_result`表：

  | rq         | shengfu |
  | ---------- | ------- |
  | 2017-04-09 | 胜      |
  | 2017-04-09 | 胜      |
  | 2017-04-09 | 负      |
  | 2017-04-09 | 负      |
  | 2017-04-10 | 胜      |
  | 2017-04-10 | 负      |
  | 2017-04-10 | 负      |

  查询结果：

  | rq         | 胜   | 负   |
  | ---------- | ---- | ---- |
  | 2017-04-09 | 2    | 2    |
  | 2017-04-10 | 1    | 2    |

  答案：

  ```SQL
  
  ```

11. 列举出你知道的HTTP请求头选项并说明其作用。

    答案：

    ```
    请求头
    ```

12. 阐述JSON Web Token的工作原理和优点。

    答案：

    ```
    JSON Web Token原理： 用户登录的时候，将用户的信息通过加密算法，生成token返回前端存储，下次浏览器访问的时候，会带token访问，后端取token进行解密，校验里面的用户信息。
    优点：用户信息存放客户端，缓解了服务器的工作压力，此外因为有用加密算法（比如sh256）保证了用户身份的安全
    ```

13. 请阐述访问一个用Django或Flask开发的Web应用，从用户在浏览器中输入网址回车到浏览器收到Web页面的整个过程中，到底发生了哪些事情，越详细越好。

    答案：

    ```
    用户在浏览器输入网址回车后，会先经过DNC服务器进行域名解析，得到对应的IP地址，之后经过nginx或apachi服务器，得到静态文件，之后经过uwsgi服务器，连接nginx和web应用，将数据返回给静态文件加以渲染，最后将内容返回给客户端。ngin可能配置负载均衡，则将端口映射到对应的端口进行查询
    ```

14. 请阐述HTTPS的工作原理，并说明该协议与HTTP之间的区别。

    答案：

    ```
    http是超文本传输协议，但是传输内容是以明文发送
    https在http的基础上加了一个安全套接字层，将传递的内容进行加密，保证了传输的安全性
    ```

15. 简述如何检查数据库是不是系统的性能瓶颈以及你在工作中是如何优化数据库操作性能的。

    答案：

    ```
    可以用慢查询查找数据库中查询超时的sql语句
    优化数据库：
    1. 创建并优化索引，组合索引才有最左原则
    2. 加缓存，将经常查询但不怎么改变的数据放缓存中
    3. 采用分区，分库，分表
    4. 配置主从数据库，主数据库负责数据添加，修改，删除。从数据库负责查询
    5. 尽量不适用全文查找，如select * 
    ```

16. 在Linux系统中，假设Nginx的访问日志位于`/var/log/nginx/access.log`，该文件的每一行代表一条访问记录，每一行都由若干列（以制表键分隔）构成，其中第1列记录了访问者的IP地址。请用一条命令找出最近的100000次访问中，访问频率最高的IP地址及访问次数。

    答案：

    ```Shell
    from functools import Counter
    with open(`/var/log/nginx/access.log`,encoding='utf-8') as f:
        Counter(line.split('   ')[0] for line in f.readlines).max_common()
    ```

