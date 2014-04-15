---
title: Space Invaders FX - Part 1
layout: post
category: code
tags: [javafx game]
---

Ohk, so I wrote this simple game in JavaFX, named it Space Invaders FX
..\
\

The entire source code for the game can be downloaded from
[here](http://worldofocean.googlepages.com/spaceinvadersfx.rar).\
\
The source code has three files, tank.fx, monster.fx and Main.fx. In
this post we will talk about tank.fx. This class controls the movements,
shooting and everything else to do with the tank. Here it is:\

~~~~
{style="border: 1px dashed rgb(153, 153, 153); padding: 5px; overflow: auto; font-family: Andale Mono,Lucida Console,Monaco,fixed,monospace; color: rgb(0, 0, 0); background-color: rgb(238, 238, 238); font-size: 12px; line-height: 14px; width: 100%; height: 300px;"}
/** tank.fx** Created on Jun 21, 2009, 9:19:12 AM*/package spaceinvadersfx;import javafx.scene.image.ImageView;import javafx.scene.image.Image;import javafx.scene.CustomNode;import javafx.scene.Node;import javafx.scene.input.KeyEvent;import javafx.scene.input.KeyCode;import javafx.scene.Group;import javafx.scene.input.MouseEvent;import javafx.scene.shape.Polygon;import javafx.scene.paint.Color;import javafx.animation.Timeline;import javafx.animation.KeyFrame;import javafx.animation.Interpolator;/*** @author Sagar Jauhari*/public class tank extends CustomNode {var monster = monsters{};var fireAgain = true;var tankX: Integer;var tankY = 400;var bulletX: Integer;var bulletY = 400;var visiblity = false;var image = ImageView {x: bind tankX, y: tankYimage: Image {url: "{__DIR__}resources/tank 50X50.png"}};var bg = ImageView {onKeyPressed: function( e: KeyEvent ) {if(e.code == KeyCode.VK_LEFT){if(tankX >= 50){    tankX-=50;}}if(e.code == KeyCode.VK_RIGHT){if(tankX <= Main.screenWidth - 100){    tankX+=50;}}}onMouseClicked: function( e: MouseEvent ):Void {fire();}image: Image {url: "{__DIR__}resources/bg.jpg"}};var bullet = Polygon {visible: bind visiblitytranslateX: bind bulletXtranslateY: bind bulletYpoints : [ 0,7, 5,0, 10,7, 10,15, 5,5, 0,15 ]fill: Color.YELLOWstroke: Color.RED}var timeline = Timeline {repeatCount: 1keyFrames : [at (0s) {bulletX => tankX+20; bulletY => tankY; visiblity => true; fireAgain=> false },at (1s) {bulletY=> -20; visiblity => true; fireAgain=> true}]}var colissionTimeline = Timeline {repeatCount: Timeline.INDEFINITEkeyFrames : [KeyFrame {    time : 0.1s    action: function(){colissionDetect()}}]}public function fire(){if(fireAgain){timeline.playFromStart();}}public function colissionDetect(){if(monster.intersects(bulletX,bulletY,10,15)){monster.isDead();}}public override function create() :Node{bg.requestFocus();colissionTimeline.play();return{Group{    content: bind[bg,image,bullet,monster]}}}}
~~~~

\
Understanding the code:\

1.  [![](http://1.bp.blogspot.com/_w1ysKIz-K98/SkJZL7jFgYI/AAAAAAAACII/ezeRRjoltOU/s200/tank+50X50.png)](http://1.bp.blogspot.com/_w1ysKIz-K98/SkJZL7jFgYI/AAAAAAAACII/ezeRRjoltOU/s1600-h/tank+50X50.png)

1.  First of all, we make an image of tank of 50X50px. Here's the image
    I made in GIMP:
2.  Next, we import it for using:\

    ~~~~
    {style="border: 1px dashed rgb(153, 153, 153); padding: 5px; overflow: auto; font-family: Andale Mono,Lucida Console,Monaco,fixed,monospace; color: rgb(0, 0, 0); background-color: rgb(238, 238, 238); font-size: 12px; line-height: 14px; width: 100%;"}
        var image = ImageView { x: bind tankX, y: tankY image: Image {     url: "{__DIR__}resources/tank 50X50.png" }};
    ~~~~

3.  Now we put a background image and add all the mouse and keyboard
    triggers to it.\

    ~~~~
    {style="border: 1px dashed rgb(153, 153, 153); padding: 5px; overflow: auto; font-family: Andale Mono,Lucida Console,Monaco,fixed,monospace; color: rgb(0, 0, 0); background-color: rgb(238, 238, 238); font-size: 12px; line-height: 14px; width: 100%;"}
     var bg = ImageView {onKeyPressed: function( e: KeyEvent ) {  if(e.code == KeyCode.VK_LEFT){      if(tankX >= 50){          tankX-=50;      }  }  if(e.code == KeyCode.VK_RIGHT){      if(tankX <= Main.screenWidth - 100){          tankX+=50;      }  }}  onMouseClicked: function( e: MouseEvent ):Void {      fire();  }  image: Image {      url: "{__DIR__}resources/bg.jpg"  }};
    ~~~~

    \

4.  Now we come to the more interesting part: the shooting! :). To
    represent a bullet, I made a polygon. The idea is to traverse this
    polygon from bottom to top by binding its y coordinate to a variable
    and linearly varying that variable with time using the Timeline
    class. Initially the bullet is invisible, then, while shooting it
    becomes visible and then again it becomes invisible. This gives the
    impression that multiple bullets are being shot contrary to the fact
    that actually, it is the same bullet again and again! Also, there is
    a constraint that at any point of time, only one bullet is in the
    scene. This is managed by the 'fireAgain' flag. See here:\

    ~~~~
    {style="border: 1px dashed rgb(153, 153, 153); padding: 5px; overflow: auto; font-family: Andale Mono,Lucida Console,Monaco,fixed,monospace; color: rgb(0, 0, 0); background-color: rgb(238, 238, 238); font-size: 12px; line-height: 14px; width: 100%;"}
        var bullet = Polygon {   visible: bind visiblity   translateX: bind bulletX   translateY: bind bulletY   points : [ 0,7, 5,0, 10,7, 10,15, 5,5, 0,15 ]   fill: Color.YELLOW   stroke: Color.RED}var timeline = Timeline {   repeatCount: 1   keyFrames : [       at (0s) {bulletX => tankX+20; bulletY => tankY; visiblity => true; fireAgain=> false },       at (1s) {bulletY=> -20; visiblity => true; fireAgain=> true}   ]}
    ~~~~

    \

5.  Finally, there's this function called fire() which fires the bullet.

    ~~~~
    {style="border: 1px dashed rgb(153, 153, 153); padding: 5px; overflow: auto; font-family: Andale Mono,Lucida Console,Monaco,fixed,monospace; color: rgb(0, 0, 0); background-color: rgb(238, 238, 238); font-size: 12px; line-height: 14px; width: 100%;"}
        public function fire(){    if(fireAgain){        timeline.playFromStart();    }}
    ~~~~

    \

So this was most of what was done with the tank. The collision detection
with the 'monster' and some other snippets not explained here will be
explained in the next post when we discuss the 'monsters.fx' class.
