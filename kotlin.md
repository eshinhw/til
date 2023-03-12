# Kotlin

Activity in Android is simple Kotlin Class. Thus, each activity can be represented by a Kotlin class. MainActivity inherits from `AppCompatActivity()`.

## **Activities and Lifecycle**

Activity in Android is simple Kotlin Class. Thus, each activity can be represented by a Kotlin class. MainActivity inherits from AppCompatActivity().

![https://user-images.githubusercontent.com/41933169/165211141-3708dbb5-fca7-4c0f-b64a-9e5c50631118.png](https://user-images.githubusercontent.com/41933169/165211141-3708dbb5-fca7-4c0f-b64a-9e5c50631118.png)

When there are multiple activities running at the same time, Android uses a STACK to manage them. The first activity executed goes to the bottom of the STACK and following activities are stacked on top of each other. When an user presses a back button, the current activity gets popped out of the stack, and returns the activity right below it.

![https://user-images.githubusercontent.com/41933169/165211071-9a2f7211-c338-4271-b3b2-1a3613d7c768.png](https://user-images.githubusercontent.com/41933169/165211071-9a2f7211-c338-4271-b3b2-1a3613d7c768.png)

- onCreate(): When activity is started, onCreate() is called.
- onStart()
- onResume(): at this point, the activity is at the top of the activity stack.
- onPause(): the activity goes to the background (guaranteed to be called, should save data onPause())
- onResume(): when the activity gets the user's focus, it starts onResume() (don't recreate it)
- onStop(): onStop is not guaranteed to be called later.
- onDestroy(): shuts down activity. If app process is killed, we have to create the activity all over again from onCreate().

## **Logcat: Solving Errors in Android Studio**

### **Types of Log Messages**

- **Verbose (Log.v)**: show all log messages
- **Debug (Log.d)**: shows all log messages related to Debug and everything else below (Info, Warn, Error and Assert)
- **Info (Log.i)**: shows all log messages related to Info and everything else below (Warn, Error, and Assert)

In similar manner, we can select which types of log messages we want to display on Logcat. We can search log messages by tags to just display what we want.

### **What We Look For in Logcat**

From Logcat, the useful information we can find is sometimes from "Caused by" clause. "Caused by" clause provides specific error messages. Also, the blue links on Logcat lead us the locations of error sources.

## **Layouts in Android**

### **Linear Layout**

We can construct a layered structure of multiple linear layouts to design an activity.

### **Density Independent Pixels (dp or dip)**

An abstract unit that is based on the physical density of the screen. These units are relative to a 160 dpi screen, so one dp is one pixel on a 160 dpi screen. The ratio of dp-to-pixel will change with the screen density, but not necessarily in direct proportion. Note: The compiler accepts both "dip" and "dp", though "dp" is more consistent with "sp".

### **Scaleable Independent Pixels (sp)**

This is like the dp unit, but it is also scaled by the user's font size preference. It is recommended you use this unit when specifying font sizes, so they will be adjusted for both the screen density and the user's preference. Note, the Android documentation is inconsistent on what sp actually stands for, one doc says "scale-independent pixels", the other says "scaleable pixels".

- padding
- match_parent vs. wrap_content
- layout_weight: When organizing multiple views over the horizontal frame, we can use layout_weight to give them unique weights.
- orientation: horizontal vs. vertical

### **Constraint Layout**

Constraint Layout helps us flatten the layout hierarchy and build simple layout designs. We don't use Expand Horizontally and Expand Vertically features because they are not reliable. The best practice with Constraint Layout is to set each constraint manually.

### **Chains and Guidelines**

- Chains + 0 widths give views equal widths horizontally.
- Helpers: Vertical or Horizontal Guidelines

## **Views in Android**

### **Buttons**

There are two ways of accessing buttons or views in Kotlin.

```
val btnABC = findViewById(R.id.btnABC) # Java way
btnABC # directly imports the id.

```

In order to directly import the ids, we need to make sure to have the following lines in build.gradle(module).

```
plugins {
    id 'com.android.application'
    id 'kotlin-android'
    id 'kotlin-android-extensions'
}

```

### **Textviews**

- textSize
- textStyle
- textAlignment

### **EditText**

- ems: If layout_width == "wrap_content", ems sets how many capital letters can be fitted into EditText (adjusts the length of EditText)
- hint
- inputType: if "number", only shows the numeric keyboard. if "textPassword", shows the keyboard for password. if "phone", shows the phone keyboard.

### **ImageView**

- scaleType

## **Intent and Multiple Activities**

- We can create `Intent()` object to go to other activities by running `startActivity(intent)`
- When sending data, we use `putExtra` and `getExtra` functions to send data.
- We can create `data class` to store data and use `Serializable` to send them to other activities.

## **Permissions**

- We can ask for permissions to users by stating `uses-permission` in `AndroidManifest` file.
- `ActivityCompat.checkSelfPermission(Context: this, Manifest.permission.WRITE_EXTERNAL_STORAGE) == PackageManager.PERMISSION_GRANTED`

## **Implicit Intents**

- `Intent(Intent.ACTION_GET_CONTENT).also {it.type = "image/*" startActivityForResult(it, request_code=0)}`
- `onActivityResult`

## **Toolbar Menus**

- `onCreateOptionsMenu(menu)` -> `menuInflator.inflate(R.menu.app_our_menu, menu)`
- `onOptionsItemSelected(item)` -> when(item.itemId)

## **Fragments**

An activity can host one or more fragments inside of it. Fragments inside an activity are affected by the life cycle of their activity. Using fragments, we don't have to create a whole new activity.

In Fragment class, there are two functions for initialization.

- `onCreateView` inflates the view of fragment.
- `onCreate`
- `onViewCreated` allows to access all the views within fragment.

Alternatively, we can pass in the id of fragment layout in Fragment().

`class FirstFragment : Fragment(R.layout.fragment_first)`

### **Static Fragments**

`android:name` allows to set the fragment we want to display.

### **Dynamic Fragments**

### **Fragment Transaction**

```
btnFragment.setOnClickListner{
  supportFragmentManager.beginTransaction().apply {
    replace(R.id.flFragment, firstFragment)
    addToBackStack(null) // navigates back to previous fragment
    commit()
  }
}
```

## **Miscellenious Tips**

- Refactor/Rename: **Shift + F6**
- Show all possible options: **Ctrl + Space**
- Rarrange XML attributes (id to the top): **Ctrl + Alt + L**
- Duplicate a line: **Ctrl + D**

## **References**

- [Android Fundamentals by Philipp Lackner](https://youtube.com/playlist?list=PLQkwcJG4YTCTq1raTb5iMuxnEB06J1VHX)

# **Kotlin Coroutines**

## **What is a Coroutine?**

A **function** is a sequence of instructions that takes inputs and gives us outputs. A **thread** describes in which context this sequence of instructions should be executed.

Running an app in a single thread has many disadvantages. This is why we are introduced the concept of multithreading.

**Multithreading** is useful for network calls and database operations which can be done in the background not affecting the UI.

## **What distinguishes Coroutines from Threads?**

**Coroutines** are light weight threads with some more extra functionalities.

- Coroutines are executed within a thread. We can start many coroutines inside a single thread.
- Coroutines are suspendable which means we can execute some instructions, pass the coroutine in the middle of execution, and let it continue when we want it to
- Coroutines can switch their context easily from one thread to another thread.

## **How to Start a Coroutine**

```
ClobalScope.launch {
    delay(3000L) // on pause for one specific coroutine
    // sleep function makes pause on all coroutines (understand the difference!)
    Log.d(TAG, "message from coroutine")
}
```

If the main thread is finished, all coroutines are automatically destroyed even the ones with on pause or on delay.

## **Suspend Functions**

`Thread.currentThread().name` prints the name of current thread

Suspend function is a function that could be started, paused, and resume. One of the most important points to remember about the suspend functions is that **they are only allowed to be called from a coroutine or another suspend function.**

## **Coroutine Contexts**

```
GlobalScope.launch(Dispatchers.PARAMETER) {}
```

- `Dispatchers.Main`: useful for UI operations in coroutine
- `Dispatchers.IO`: related to data operations (networking, database, writing to files)
- `Dispatchers.Default`
- `Dispatchers.Unconfined`
- `newSingleThreadContext("MyThread")`: custom thread context

`withContext(Dispatchers.Main)` changes thread.

## **runBlocking**

`runBlocking` actually blocks the main thread. It can be used for accessing suspend function from the main thread.

```
runBlocking {
    launch {
        // synchronized code blocks
    }
    Log.d(TAG, "Start of runBlocking")
    delay(5000L) // dealy function can be called inside runBlocking
    Log.d(TAG, "End of runBlocking")
}
```

the `launch` blocks inside `runBlocking` are synchronized which means they are executed at the same time.

## **Jobs, Waiting and Cancellation**

```
val job = GlobalScope.launch(Dispatchers.Default) {
    // repeat is a suspend function
    repeat(5) {
        Log.d(TAG, "Coroutine is still running...)
        delay(1000L)
    }
}

runBlocking {
    job.join() // join function makes the main thread wait until job is finished
    job.cancel() // cancel function cancels the job immediately
    Log.d(TAG, "Main Thread is continuing...")
}
```

- `isActive`: check whether the coroutine job is still active.
- `withTimeout(3000L)`: cancel the job after 3 seconds

## **Async and Await**

When there are several suspend functions, they are normally executed in sequence.

`measureTimeMillis`: measure the total time of execution in ms.

```
val time = measureTimeMillis {
    val answer1 = networkCall1()
    val answer2 = networkCall2()

    Log.d(TAG, "Answer1 is $answer1")
    Log.d(TAG, "Answer2 is $answer2")
}
Log.d(TAG, "Requests took $time ms")
```

With `Async` and `Await`

```
val time = measureTimeMillis {
    val answer1 = async{ networkCall1() }
    val answer2 = async{ networkCall2() }

    Log.d(TAG, "Answer1 is $answer1.await()")
    Log.d(TAG, "Answer2 is $answer2.await()")
}
Log.d(TAG, "Requests took $time ms")
```

## **lifecycleScope and viewModelScope**

- `GlobalScope` runs coroutines in global scope over other activities. GlobalScope may cause resource leaks while running in the back when we work on other activities.
- `lifecycleScope` only lives in the life cycle of the activity where it was initiated.
- `viewModelScope` only lives as long as the viewModel is alive.

## **Coroutines with Firebase Firestore**

## **Coroutines with Retrofit**

## **References**
