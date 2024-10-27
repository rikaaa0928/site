---
title: "Rust tokio: Send与Sync"
date: 2024-10-27T19:15:00+08:00
draft: false
tags: ["rust", "learning", "tokio", "async"]
author: ["rikaaa0928"]
categories : ["code"]
---
tokio中，返回的future无脑实现Send，因为tokio异步框架并不能保证单个异步任务绑定某个真实线程执行，实现Send表示这个future可以安全的跨线程执行。  
Sync表示并发安全，需要跨异步任务调用的必须是Sync，可以套Mutex实现非Sync转Sync，再套Arc实现clone。  

// Sync 类型:  
Arc<T>         // 当 T: Sync  
Mutex<T>       // 当 T: Send  
RwLock<T>      // 当 T: Send  
AtomicBool  
AtomicI32  
Vec<T>         // 当 T: Sync  
String  
&T             // 当 T: Sync  

// 非 Sync 类型:  
RefCell<T>     // 内部可变性不是线程安全的  
Cell<T>        // 同上  
Rc<T>          // 引用计数不是线程安全的  
*mut T         // 裸指针  