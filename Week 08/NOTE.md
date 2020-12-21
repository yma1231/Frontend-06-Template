# 学习笔记

## URL -> Bitmap

1. URL, HTML(parse), DOM, DOM w. CSS, DOM w. Position, Bitmap

## 状态机

1. 状态机保存状态，核心函数

function match(str) {
    let state = start;
    for (let c of str) {
        state = state(c); // IMPORTANT
    }
    return state === end;
}

## HTTP server and client

### HTTP REQUEST

1. Request: Method(GET/PUT/POST/DELETE/OPTION)

1. Header: Content-Type: (required)

1. Body: depends on Content-Type, KeyValue.

### Send Func

1. 在Request函数里面，收集必要信息

1. async的，返回promise

### HTTP RESPONSE

1. Status Line: 状态码 200, 404, 500相关，304, 403等等

1. Headers: content-type, ...

1. Body: chunk（16进制数字， 内容，十进制一个0结尾）

### send request

1. 支持已有connection或create new connection

1. 收到数据，传给paser

1. 根据parser， resolve promise

### ResponseParser

1. Response必须分段构造，用ResponseParser来装配

1. ResponseParser分段处理ResponseText， 用状态机分析文本结构。

### BodyParser

1. Response body根据content-type有不同结构，采用子parser结构

1. 以trunkedBodyParser为例，用状态机处理body的格式



