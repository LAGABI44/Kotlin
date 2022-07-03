# 웹뷰 확장(상단바 없애기, 새창 열리지 않게)

## 01. 웹앱 테스트 gif
![webview_Test2](https://user-images.githubusercontent.com/96757866/177030936-b1f82a17-aec9-4206-9e32-8062e90c6394.gif)



## 02. 웹뷰 설정하기

### (1) 프로젝트 이름 제거
- res/values/themes.xml 에 코드 추가
![webview01](https://user-images.githubusercontent.com/96757866/177030854-359b6b27-bca6-4194-95ac-0bef7d0b9a79.png)
```
<item name="windowNoTitle">true</item>
```


### (2) 새창 열리지 않게 설정
- MainActivity.kt 설정
![webview02](https://user-images.githubusercontent.com/96757866/177030873-5197a680-57ca-493b-91a3-6f7d456cbcfe.png)

```
myWebView.webViewClient = WebViewClient()
```

### (3) 뒤로가기 설정
![webview01](https://user-images.githubusercontent.com/96757866/177030877-70be62e4-a3d3-44b8-9ee3-cf639853643b.png)

```
override fun onKeyDown(keyCode: Int, event: KeyEvent?): Boolean {
        // Check if the key event was the Back button and if there's history
        val myWebView: WebView = findViewById(R.id.main_webview)
        if (keyCode == KeyEvent.KEYCODE_BACK && myWebView.canGoBack()) {
            myWebView.goBack()
            return true
        }
        // If it wasn't the Back key or there's no web page history, bubble up to the default
        // system behavior (probably exit the activity)
        return super.onKeyDown(keyCode, event)
```


## Reference
- https://developer.android.com/guide/webapps/webview#kotlin
