---
id: 571
title: 'Create Counter Using TextView &#8211; Android'
date: 2013-12-13T20:08:23+00:00
author: Joel
excerpt: This is yet another simple Android tutorial that lets you display a counter with a delay of one second. The example updates a TextView every one second until it has reached the count 0. The counter is initially set to start from 10.
layout: post
guid: http://www.joelifernandes.com/?p=571
permalink: /android/create-counter-using-textview-android/
dsq_thread_id:
  - "2327699054"
post_views_count:
  - "650"
categories:
  - Android
tags:
  - Android
---
This is yet another simple Android tutorial that lets you display a counter with a delay of one second. This question was asked on StackOverflow <a href="http://stackoverflow.com/questions/20292760/display-values-dynamically-in-textview-android/20293383" target="_blank">here</a>.

The example updates a TextView every one second until it has reached the count 0. The counter is initially set to start from 10.

    int i = 10; //declare this globally
    final Handler handler = new Handler();
    handler.postDelayed(new Runnable() {
        @Override
        public void run() {
            if(i != 0) { 
                    text.append(" " + i);
                    i--;
                    handler.postDelayed(this, 1000);
                } else {
    		handler.removeCallbacks(this);
                    text.append(" Stopped");
                }
            }
        }, 1000);
    }
    

Make sure that you declared `int i = 10;` globally. The answer was originally posted <a href="http://stackoverflow.com/a/20293383/3025732" target="_blank">here</a>.