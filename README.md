example of thundering herd in epoll   

epoll_create() --> fork()  --> epoll_wait()   


# connect to epoll server

#telnet 127.0.0.1 8888

# output

Create worker 1   
Create worker 2   
Create worker 3   
Create worker 4   
   
  
#### Condition 1: single process was awaken   

worker 1 return from epoll_wait!
worker 1 accept successed!

#### Condition 2: multiple processes was awaken    

worker 1 return from epoll_wait!    
worker 1 accept successed!    
worker 0 return from epoll_wait!    
worker 0 accept failed!    


worker 0 return from epoll_wait!    
worker 0 accept successed!    
worker 1 return from epoll_wait!   
worker 3 return from epoll_wait!   
worker 3 accept failed!   
worker 1 accept failed!    
