---
title: "Rust: 可变和引用"
date: 2024-01-10T09:40:00+08:00
draft: false
tags: ["rust", "learning"]
author: ["rikaaa0928"]
categories : ["code"]
---
### `mut a: &mut i32`  
`mut a`表示`a`可变，可以被重新绑定  
`&`表示(不可变)引用
`&mut`表示可变引用，即`*a`可变，可以被重新绑定  

### 测试验证代码
```
fn change_i_mut_ref(i:&mut i32){
    *i=2; // 给引用绑定新值，i 不可变，*i 指向的变量可变
}

// fn change_i_mut_ref_err(i:&mut i32){
//     i=xxxx; // i 不可变，不可重新绑定，等于什么都不行
// }

fn change_mut_i(mut i:i32){
    i=4;
}

fn change_mut_i_ref(mut i:&i32){
    i=&5;
}

fn change_mut_i_mut_ref_change_i(mut i:&mut i32){
    // i=&5; //会报错，因为 &5 的类型是 &i32, &mut 5 的类型是 &mut i32
    // i=&mut 5; //一样会报错，因为 &mut 5 生命周期仅在函数内，函数返回后，i引用的值会被回收
}

fn change_mut_i_mut_ref_change_ref(mut i:&mut i32){
    *i=7;
}

#[tokio::test]
async fn my_test1()-> crate::Result<()> {
    let mut i=1i32;
    println!("{}",i);
    change_i_mut_ref(&mut i);// 这里需要传 &mut i, &i的类型是 &i32, 不是 &mut i32，同时i需要是mut i，不可变变量不可转化为可变引用
    println!("{}",i);
    change_mut_i(i);//修改失败
    println!("{}",i);//修改失败
    change_mut_i_ref(&mut &i);
    println!("{}",i);//修改失败
    change_mut_i_mut_ref_change_i(&mut i);
    println!("{}",i);//修改失败
    change_mut_i_mut_ref_change_ref(&mut i);
    println!("{}",i);//修改成功，和change_i_mut_ref等效
    Ok(())
}
```