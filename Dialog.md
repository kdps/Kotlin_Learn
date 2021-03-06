# 1. Dialog Control

## 1.1. Show Dialog (With DataBinding)

Warning : `Do not use android:onClick Event in Layout XML File When Use Dialog`

```Kotlin
val mDialogBinding: LayoutBasicBinding = DataBindingUtil.inflate(getSystemService(Context.LAYOUT_INFLATER_SERVICE) as LayoutInflater, R.layout.layout_basic, null, false)
var mDialog = Dialog(mActivity)
mDialog.requestWindowFeature(Window.FEATURE_NO_TITLE)
mDialog.window.setBackgroundDrawable(ColorDrawable(Color.TRANSPARENT))

mDialogBinding.btnClose.setOnClickListener {v ->
    mDialog.dismiss()
}

mDialog.setContentView(mDialogBinding.root)

mDialog.setCancelable(true)
mDialog.show()
```

# 2. Data Control

## 2.1. Get Data Of Dialog

```Kotlin
mDialogBinding.btnSubmit.setOnClickListener {v ->
    var content = (mDialogBinding.submitContent as EditText).text.toString()
}
```

# 3. Window Control

## 3.1. Get Size of Dialog

### 3.1.1. Get DisplayMetrics

```Kotlin
fun getDisplayMetrics() {
    val displayMetrics = DisplayMetrics()
    windowManager.defaultDisplay.getMetrics(displayMetrics)
    
    return displayMetrics
}
```

### 3.1.2. Get DIsplay Pixels

```Kotlin
fun getWidthPixels() {
    var displayMetrics = getDisplayMetrics()
    val displayWidth = displayMetrics.widthPixels
    return displayWidth
}

fun getWidthPixels() {
    var displayMetrics = getDisplayMetrics()
    val displayWidth = displayMetrics.heightPixels
    return displayWidth
}
```

### 3.1.3. Get Dialog Window Size

```Kotlin
fun getWindowAttributes(mDialog: Dialog) {
    return mDialog.window!!.attributes
}

fun getWindowWidth(mDialog: Dialog) {
    return getWindowAttributes(mDialog).width
}

fun getWindowHeight(mDialog: Dialog) {
    return getWindowAttributes(mDialog).height
}
```

## 3.2. Set Dialog Size

### 3.2.1. Set Attributes of Dialog Windows Size

```Kotlin
var params = getWindowAttributes(mDialog)
params.width = getWindowWidth(mDialog)
params.height = getWindowHeight(mDialog)
mDialog.window!!.attributes = params
```

### 3.2.2 Use Layout Parameter

```Kotlin
var params = getWindowAttributes(mDialog)
params.width = WindowManager.LayoutParams.WRAP_CONTENT
params.height = WindowManager.LayoutParams.MATCH_PARENT
mDialog.window!!.attributes = params
```
