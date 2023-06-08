# Quizzler-Android
<div>
<img src="https://github.com/PratyayMallik1006/Quizzler-Android/blob/main/Quizzler1.jpeg?raw=true" height="600" style="float: left">
<img src="https://github.com/PratyayMallik1006/Quizzler-Android/blob/main/Quizzler2.jpeg?raw=true" height="600" style="float: left">
</div>

## Notes:

# Toast
```java
Toast.makeText(getApplicationContext(),"Hello",Toast.LENGTH_SHORT).show();
```
# Progress Bar
1. activity_main.xml 
```xml
<ProgressBar
android:layout_width="fill_parent"
android:layout_height="wrap_content"
android:id="@+id/progress_bar"
android:indeterminate="false"  />
```
2. MainActivity.java
```java
int  PROGRESS_BAR_INCREMENT = (int)Math.ceil(100.0/mQuestionBank.length);
ProgressBar mProgressBar=(ProgressBar) findViewById(R.id.progress_bar);
mProgressBar.incrementProgressBy(PROGRESS_BAR_INCREMENT);
```
# Screen Rotation
1. Fixing to portrait mode
- Goto **Manifests>AndroidManifest.xml**
```xml
<activity android:name=".MainActivity"
        android:screenOrientation="portrait">
		...
</activity>
```
2. onSaveInstanceState
```java
@Override
protected  void  onCreate(Bundle  savedInstanceState) {
	super.onCreate(savedInstanceState);
	setContentView(R.layout.activity_main);
	if(savedInstanceState != null){
		score = savedInstanceState.getInt("ScoreKey");
	} else {
		score=0;
	}
}

@Override
public void onSaveInstanceState(Bundle outState){
	super.onSaveInstanceState(outState);
	
	outState.putInt("ScoreKey", score);
}
```

# Alert Dialogue
```java
AlertDialog.Builder alert = new AlertDialog.Builder(getApplicationContext());
```
Or
```java
AlertDialog.Builder alert = new AlertDialog.Builder(this);
alert.setTitle("Game Over");
alert.setCancelable(false);
alert.setMessage("Your Score is:"+ score);

alert.setPositiveButton(``"Yes"``, (DialogInterface.OnClickListener) (dialog, which) -> {
	finish();
});

alert.setNegativeButton(``"No"``, (DialogInterface.OnClickListener) (dialog, which) -> {
	dialog.cancel();
});

alert.show();

```
