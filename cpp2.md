---
title: '[C++]线程'
date: 2020-04-08 23:01:42
tags: c++
---
#### 获取线程id
```
#include <pthread.h>
int GetTid() {
    return pthread_self();
}
```
#### 获取和设置线程名称
```
#include <sys/prctl.h>
std::string GetName() {
    char name[256] = { 0 };
    prctl(PR_GET_NAME, name);
    return name;    
}

void SetName(const std::string &name) {
    prctl(PR_SET_NAME, name.c_str());
}
```
#### 分离线程
C++11
```
#include <thread>
void StartDetach(const std::function<void()> &func) {
    thread([=]() {
        func();
    }).detach();    
}
```