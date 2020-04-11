---
title: '[C++]宏'
date: 2020-04-08 00:44:45
tags: c++
---
#### 使用宏校验值为真
不带返回值
```
#define CM_CHECK_VAL(val) \
    if (!(val)) { \
        return; \
    }

void test(int *num) {
    CM_CHECK_VAL(num);
    cout << *num << endl;
}
```
带返回值
```
#define CM_CHECK_VAL_RET(val, ret) \
    if (!(val)) { \
        return ret; \
    }

bool test(int *num) {
    CM_CHECK_VAL(num, false);
    cout << *num << endl;
    return true;
}
```
#### 使用宏校验枚举在范围内
校验枚举是否有效并返回
```
#define CM_CHECK_ENUMTYPE(EnumType, val) \
    if (val < 0) return; \
    if (val >= EnumType##_Cnt) return;

#define CM_CHECK_ENUMTYPE_RET(EnumType, val, ret) \
    if (val < 0) return ret; \
    if (val >= EnumType##_Cnt) return ret;
```
只判断
```
#define CM_IS_ENUMTYPE(EnumType, val) (val >= 0 && val < EnumType##_Cnt ? true : false)
```
#### 使用宏操作内存
初始化结构体
```
#define CM_INIT_STRUCT(t) memset(&t, 0, sizeof(t))
#define CM_INIT_STRUCT_PTR(t) memset(t, 0, sizeof(*t))
```
释放指针
```
#define CM_FREE_PTR(p) \
    if (p) { \
        free(p); \
        p = nullptr; \
    }
```
