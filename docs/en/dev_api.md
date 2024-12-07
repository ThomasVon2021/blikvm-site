# API

!!! warning "DISCLAIMER: This API is experimental and subject to change at any moment! This document is only valid for v1.4.0 and earlier versions, and will be updated soon"

This document is the HTTP API development manual for BLIKVM OS. If you have new API requirements not covered in this document, you can submit a pull request on GitHub to seek support. Please replace the kvmip in the request URL with the actual IP address of your KVM.

### **Authentication**

This API is used for user login and returns an access token. This token expires after 12 hours and can be presented as a bearer token for APIs that require authentication.

- Request URL: `https://kvmip/api/login`
- Request Method: POST
- Request Body: JSON format, for example:

```
{
    "username": "admin",
    "password": "admin"
}
```

The response is as follows; if the status is not 1, the authentication has failed.

```
{
    "status": 1,
    "info": "login success",
    "data": {
        "token": "2sscdada6a97a774fcd4714c"
    }
}
```

### **MJPEG Video**

This API is used to obtain the MJPEG video stream when the image mode is set to MJPEG.  

- Request URL: `http://kvmip:8008/stream`  

This API is used to capture a frame of MJPEG in image mode.

- Request URL: `http://kvmip:8008/snapshot`  
- Request Method: GET

### **Keyboard**  

??? info "For specific keyboard encoding, please refer to the following:"
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

- Request URL: `http://kvmip/keyboard`  
- Request Method: GET  
- Request Body: JSON format, where "keycodes" is a string array supporting multiple inputs at once. For example:

```
{
    "keycodes": ["Digit1"]
}
```  

The response result is as follows:

```
{
    "status": 1,
    "info": "key input success",
    "data": []
}
```
