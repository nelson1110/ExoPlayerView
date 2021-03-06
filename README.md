# ExoPlayerView
ExoPlayerView is a simple video view based on [ExoPlayer](https://github.com/google/ExoPlayer).

[中文](/README_CN.md).

![brightness](/images/brightness.png)![controller_1](/images/conroller_1.png)
![fast_forward_rewind](/images/fastforward_rewind.png)![landscape](/images/landscap.png)
![portrait](/images/portrait.png)![volume](/images/volume.png)

I already add this lib to jcenter.We can use this lib in `build.gradle` once
it was passed.

ExoPlayerView can play simple video directly, such as mp4,m3u8 and so on.
It's easy to use.
Just declare ExoPlayerVIew in your layout files:
```xml

    <com.jarvanmo.exoplayerview.ui.ExoVideoView
        android:id="@+id/videoView"
        android:layout_width="match_parent"
        android:layout_height="300dp"
        app:useController="true"
        app:resizeMode="fit"
        />
        
```
The ExoPlayerView provide 3 modes to resize your video: fit ,  fit_width , fit_height
and none.

We can play a video just like:
```java
   videoView.play(mediaSource);
```
also we can give a display name:
```java
 mediaSource.setDisplayName("LuYu YouYue");
```
or;
```java
 videoView.setDisplayName("LuYu YouYue");
```


There are also some listeners for you :
```java

        videoView.setBackListener(new ExoVideoPlaybackControlView.ExoClickListener() {
            @Override
            public void onClick(View view, boolean isPortrait) {
                if(isPortrait){
                    finish();
                }else {
                    videoView.changeOrientation();
                }
            }
        });

```

```java
        videoView.setFullScreenListener(new ExoVideoPlaybackControlView.ExoClickListener() {
            @Override
            public void onClick(View view, boolean isPortrait) {
                videoView.changeOrientation();
            }
        });
```
Note:The method `changeOrientation()` only determine the style of the 
playback controller view.


Also you can add you view to the controller view when landscape:

```java
       videoView.addViewToControllerWhenLandscape(view);
```
the view you want to add will add into FrameLayout．

The ExoPlayer also support simple gesture action, such as change-volume,
change-brightness and so on.If your target SDK version is 23
or higher, don't forget to request the following permission:
```xml
<uses-permission android:name="android.permission.WRITE_SETTINGS"/>
```