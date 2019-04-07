---
id: 577
title: 'YouTube Android Player API &#8211; Play Videos with &#8220;start&#8221; and &#8220;end&#8221;'
date: 2014-02-16T00:44:12+00:00
author: Joel
excerpt: |
  This tutorial helps you specify "start" and "end" parameters to play video using YouTube Android Player API. YouTube allows you set the start and end time of a video by specifiying the parameters "start" and "end" in the video URL.
  
  For instance, take a look at this URL: https://www.youtube.com/v/BmOpD46eZoA?start=36&end=65
  
  If you open the video click, you will notice that the video starts playing from the 36th second and stops at the 65th second.
layout: post
guid: http://www.joelifernandes.com/?p=577
permalink: /android/youtube-android-player-api-play-videos-start-end/
dsq_thread_id:
  - "2322451582"
post_views_count:
  - "739"
categories:
  - Android
tags:
  - Android
  - YouTube
---
YouTube allows you set the start and end time of a video by specifiying the parameters &#8220;start&#8221; and &#8220;end&#8221; in the video URL.

For instance, take a look at this URL:

`<a href="https://www.youtube.com/v/BmOpD46eZoA?start=36&end=65" target="_blank">https://www.youtube.com/v/BmOpD46eZoA?start=36&end=65</a>`

If you open the video click, you will notice that the video starts playing from the 36th second and stops at the 65th second.

I&#8217;m not sure if there exists any direct method that gives this kind of functionality with the YouTube Android Player API. However, if there is/are any such direct implementation/s, please feel free to comment below and I will update the post.

#### The Workaround

To implement a similar functionality with YouTube Android Player API there needs a little workaround to be done. In my example, I&#8217;ve used a Handler and the Runnable interface to keep a track of the video&#8217;s current time (in milliseconds). Every second, a condition is checked to see if the video&#8217;s (current) time has reached the user specified end time.

Note: This was a <a href="http://stackoverflow.com/questions/20565494/how-to-provide-start-and-end-parameters-for-a-youtube-video-in-youtube-android-p/20573629" target="_blank">question</a> posted on StackOverflow and this was my <a href="http://stackoverflow.com/a/20573629/3025732" target="_blank">answer</a> to it.

Let&#8217;s take a look at the implementation:

<pre class="brush: java; title: ; notranslate" title="">final Handler handler = new Handler();
handler.postDelayed(new Runnable() {
@Override
public void run() {
//For every 1 second, check the current time and endTime
if(MyActivity.player.getCurrentTimeMillis() &lt;= endTime) {
text.setText("Video Playing at " + MyActivity.player.getCurrentTimeMillis());
handler.postDelayed(this, 1000);
} else {
handler.removeCallbacks(this); //no longer required
text.setText(" Reached " + endTime);
MyActivity.player.pause(); //and Pause the video
}
}
}, 1000);
</pre>

Here&#8217;s the complete Activity code:

<pre class="brush: java; title: ; notranslate" title="">public class MyActivity extends YouTubeBaseActivity implements YouTubePlayer.OnInitializedListener{

public static final String API_KEY = "YOUR_API_KEY_HERE";
public static final String VIDEO_ID = "yeF_b8EQcK0";
private static YouTubePlayer player;

TextView text;

//this is the end time in milliseconds (65th second)
public int endTime = 65000;

@Override
protected void onCreate(Bundle savedInstanceState) {
super.onCreate(savedInstanceState);
setContentView(R.layout.my_activity);
text = (TextView) findViewById(R.id.text);
YouTubePlayerView youTubePlayerView = (YouTubePlayerView)findViewById(R.id.youtubeplayerview);
youTubePlayerView.initialize(API_KEY, this);
}

@Override
public void onInitializationFailure(Provider provider,
YouTubeInitializationResult result) {
Toast.makeText(getApplicationContext(),
"onInitializationFailure()",
Toast.LENGTH_LONG).show();
}

@Override
public void onInitializationSuccess(Provider provider, YouTubePlayer player, boolean wasRestored) {

MyActivity.player = player; //necessary to access inside Runnable

//start the video at 36th second
player.loadVideo(VIDEO_ID, 36000);

final Handler handler = new Handler();
handler.postDelayed(new Runnable() {
@Override
public void run() {
//For every 1 second, check the current time and endTime
if(MyActivity.player.getCurrentTimeMillis() &lt;= endTime) {
text.setText("Video Playing at " + MyActivity.player.getCurrentTimeMillis());
handler.postDelayed(this, 1000);
} else {
handler.removeCallbacks(this); //no longer required
text.setText(" Reached " + endTime);
MyActivity.player.pause(); //and Pause the video
}
}
}, 1000);
}
}
</pre>