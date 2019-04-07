---
id: 558
title: Find and Colorize Specific Words (Hashtags) in a String (TextView)
date: 2013-11-28T01:27:21+00:00
author: Joel
excerpt: |
  A user on Stack Overflow came up with an interesting problem to find and colorize specific words that are hashtags in a given string extracted from a TextView.
  
  The solution is quite simple to achieve unless you’re new to Android development or Java programming.
  
  The problem was that the user wanted to identify or match hashtags from a given text (in a TextView) and colorize every hashtag in it. Well, this has a very simple approach and can be achieved easily with a just a few lines of code.
layout: post
guid: http://www.joelifernandes.com/?p=558
permalink: /android/find-color-hashtags-in-textview/
dsq_thread_id:
  - "2328852520"
post_views_count:
  - "604"
categories:
  - Android
tags:
  - Android
  - Code
---
A user on <a href="http://stackoverflow.com/a/20251261/3025732" target="_blank">Stack Overflow</a> came up with an interesting problem to find and colorize specific words that are hashtags in a given string extracted from a TextView.

The solution is quite simple to achieve unless you’re new to Android development or Java programming.

The problem was that the user wanted to identify or match hashtags from a given text (in a TextView) and colorize every hashtag in it. Well, this has a very simple approach and can be achieved easily with a just a few lines of code.

Here’s the final output what the user wanted:

<img class="size-full wp-image-561 alignnone" alt="Find and Color Hashtag in TextView" src="http://www.joelifernandes.com/wp-content/uploads/2013/11/find-color-hashtag-textview.png" width="720" height="332" srcset="http://joelifernandes.com/wp-content/uploads/2013/11/find-color-hashtag-textview-300x138.png 300w, http://joelifernandes.com/wp-content/uploads/2013/11/find-color-hashtag-textview.png 720w" sizes="(max-width: 720px) 100vw, 720px" /> 

Here’s the sample code which will obtain the string from the TextView, and using Java’s in-built java.util.regex.Pattern class, we can define a pattern that we would like to find in the string. With the help of Matcher class, we will find for the exact alphanumeric pattern that begin with the hash symbol.

When an appropriate match is found, we set the color of the particular pattern by passing the start and end index value.

<pre><pre class="brush: java; title: ; notranslate" title="">&lt;br /&gt;SpannableString hashText = new SpannableString(text.getText().toString());&lt;br /&gt;Matcher matcher = Pattern.compile("#([A-Za-z0-9_-]+)").matcher(hashText);&lt;br /&gt;while (matcher.find()) {&lt;br /&gt;&lt;%%KEEPWHITESPACE%%&gt;        hashText.setSpan(new ForegroundColorSpan(Color.BLUE), matcher.start(), matcher.end(), 0);&lt;br /&gt;}&lt;br /&gt;text.setText(hashText);&lt;br /&gt;</pre>


<p>
  Hope this helps to anyone else who is finding a way to do it.
</p>