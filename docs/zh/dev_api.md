# **API**

!!! warning "申明: 此API为实验性的，任何时候都有可能被改变!此文档只在v1.4.0和之前版本有效，即将更新."

此文档为BLIKVM OS的http API开发手册，若您有新的API需求不在此文档中，可以在github中提pr获得支持。请求URL中的kvmip需根据你kvm的ip实际替换。

### **登录认证**
此API用于用户登录，并返回访问令牌。后续有的api均需要token令牌。   

- 请求URL: `http://kvmip/login_api`  
- 请求方法: GET  
- 请求体: JSON 格式,如:    
```
{
    "username": "admin",
    "password": "admin"
}
```
响应结果如下，若status不为1，则认证失败。
```
{
    "status": 1,
    "info": "login success",
    "data": {
        "token": "2sscdada6a97a774fcd4714c"
    }
}
```

### **ATX开关机**
此API用于控制目标设备开关机，和重启。
- 请求URL: `http://kvmip/atx`  
- 请求方法: POST  
- 请求体: JSON 格式:  
1. 其中cmd为128为开关机(即开机的情况下模拟的为短按关机，关机的情况下为短按开机);  
2. 192为强制关机(模拟长按强制关机);  
3. cmd为8表示重启。如:    
```
{
    "cmd": 128
}
```
响应结果如下，若status不为1，则失败。
```
{
    "status": 1,
    "info": "success",
}
```


### **mjepg图像**
此API用于在图像模式为mjepg的模式下，拿到mjpeg的视屏流。     
- 请求URL: `http://kvmip:8008/stream` ，此API用于在图像模式为mjepg的模式下，拿到mjpeg的一帧图片。   
- 请求URL: `http://kvmip:8008/snapshot`    
- 请求方法: GET 

### **键盘**  

??? info "键盘具体编码可参考"
    ```
    "KeyA"=> 4,
    "KeyB"=> 5,
    "KeyC"=> 6,
    "KeyD"=> 7,
    "KeyE"=> 8,
    "KeyF"=> 9,
    "KeyG"=> 10,
    "KeyH"=> 11,
    "KeyI"=> 12,
    "KeyJ"=> 13,
    "KeyK"=> 14,
    "KeyL"=> 15,
    "KeyM"=> 16,
    "KeyN"=> 17,
    "KeyO"=> 18,
    "KeyP"=> 19,
    "KeyQ"=> 20,
    "KeyR"=> 21,
    "KeyS"=> 22,
    "KeyT"=> 23,
    "KeyU"=> 24,
    "KeyV"=> 25,
    "KeyW"=> 26,
    "KeyX"=> 27,
    "KeyY"=> 28,
    "KeyZ"=> 29,
    "Digit1"=> 30,
    "Digit2"=> 31,
    "Digit3"=> 32,
    "Digit4"=> 33,
    "Digit5"=> 34,
    "Digit6"=> 35,
    "Digit7"=> 36,
    "Digit8"=> 37,
    "Digit9"=> 38,
    "Digit0"=> 39,
    "Enter"=> 40,
    "Escape"=> 41,
    "Backspace"=> 42,
    "Tab"=> 43,
    "Space"=> 44,
    "Minus"=> 45,
    "Equal"=> 46,
    "BracketLeft"=> 47,
    "BracketRight"=> 48,
    "Backslash"=> 49,
    "Semicolon"=> 51,
    "Quote"=> 52,
    "Backquote"=> 53,
    "Comma"=> 54,
    "Period"=> 55,
    "Slash"=> 56,
    "CapsLock"=> 57,
    "F1"=> 58,
    "F2"=> 59,
    "F3"=> 60,
    "F4"=> 61,
    "F5"=> 62,
    "F6"=> 63,
    "F7"=> 64,
    "F8"=> 65,
    "F9"=> 66,
    "F10"=> 67,
    "F11"=> 68,
    "F12"=> 69,
    "PrtSc"=> 70,
    "ScrollLock"=> 71,
    "Pause"=> 72,
    "Insert"=> 73,
    "Home"=> 74,
    "PageUp"=> 75,
    "Delete"=> 76,
    "End"=> 77,
    "PageDown"=> 78,
    "ArrowRight"=> 79,
    "ArrowLeft"=> 80,
    "ArrowDown"=> 81,
    "ArrowUp"=> 82,
    "NumLock"=> 83,
    "NumpadDivide"=> 84,
    "NumpadMultiply"=> 85,
    "NumpadSubtract"=> 86,
    "NumpadAdd"=> 87,
    "NumpadEnter"=> 88,
    "Numpad1"=> 89,
    "Numpad2"=> 90,
    "Numpad3"=> 91,
    "Numpad4"=> 92,
    "Numpad5"=> 93,
    "Numpad6"=> 94,
    "Numpad7"=> 95,
    "Numpad8"=> 96,
    "Numpad9"=> 97,
    "Numpad0"=> 98,
    "NumpadDecimal"=> 99
    ```

- 请求URL: `http://kvmip/keyboard`  
- 请求方法: GET  
- 请求体: JSON 格式,keycodes为字符串数组，支持一次输入多个,如:    
```
{
    "keycodes": ["Digit1"]
}
```


响应结果如:
```
{
    "status": 1,
    "info": "key input success",
    "data": []
}
```
