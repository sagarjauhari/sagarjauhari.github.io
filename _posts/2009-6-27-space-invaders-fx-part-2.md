---
title: Space Invaders FX - Part 2
layout: post
category: code
tags: [javafx game]
---

\
\
\
So, continuing with my last post where I described the 'tanks' class, we
will discuss the 'monster' class in this post:\

~~~~
{style="border: 1px dashed rgb(153, 153, 153); padding: 5px; overflow: auto; font-family: Andale Mono,Lucida Console,Monaco,fixed,monospace; color: rgb(0, 0, 0); background-color: rgb(238, 238, 238); font-size: 12px; line-height: 14px; width: 100%; height: 300px;"}
/** monsters.fx** Created on Jun 21, 2009, 9:28:33 AM*/package spaceinvadersfx;import javafx.animation.KeyFrame;import javafx.animation.Timeline;import javafx.scene.CustomNode;import javafx.scene.Group;import javafx.scene.image.Image;import javafx.scene.image.ImageView;import javafx.scene.Node;import javafx.scene.paint.Color;import javafx.scene.shape.Polygon;import javafx.scene.transform.Rotate;import spaceinvadersfx.Main;/*** @author Sagar Jauhari*/public class monsters extends CustomNode {var bulletX: Integer;var bulletY: Integer;public var monsterX: Integer;public var monsterY: Integer = 10;var animationRate = 1;var visiblity = true;var bulletVisiblity = false;var rotation = 0;var image = ImageView {x: bind monsterXy: bind monsterYvisible: bind visiblityimage: Image {url: "{__DIR__}resources/monster.png"}transforms: Rotate { pivotX : bind monsterX+25, pivotY : bind monsterY+25, angle: bind rotation }}var timeline = Timeline {rate: bind animationRate;repeatCount: Timeline.INDEFINITEautoReverse: truekeyFrames : [at (0s) {monsterX => 0;},at (4s) {monsterX => 440;}]}var attackTimeline = Timeline {repeatCount: 1keyFrames : []}function attack(){var bullet = Polygon {transforms: Rotate { pivotX : 5, pivotY : 0.8, angle: 180 }visible: bind bulletVisiblitytranslateX: bind bulletXtranslateY: bind bulletYpoints : [ 0,7, 5,0, 10,7, 10,16, 5,5, 0,16 ]fill: Color.YELLOWstroke: Color.RED}}public function isDead(){timeline.pause();var isDeadTimeline = Timeline {repeatCount: 1keyFrames : [   at (0s){rotation => 0},   at (0.2s){rotation => 180;},   KeyFrame {       time: 0.6s       action: function(){           Main.score+=15;           rotation = 0;           timeline.playFromStart();       }   }]};isDeadTimeline.play();}public override function create(): Node {timeline.play();return Group {content: bind [image]};}}
~~~~

Understanding the code:\

1.  We make an ImageView object for the monster and bind the x and y
    coordinates
    [![](http://4.bp.blogspot.com/_w1ysKIz-K98/SkWu0As8xJI/AAAAAAAACJw/llH3YzNypdI/s200/monster.png)](http://4.bp.blogspot.com/_w1ysKIz-K98/SkWu0As8xJI/AAAAAAAACJw/llH3YzNypdI/s1600-h/monster.png)to
    variables to allow movement. Also, the 'rotation' transformation is
    added which will be used to animate the monster when it dies ( it
    turns upside down when the isDead() function is called! :) ).

    ~~~~
    {style="border: 1px dashed rgb(153, 153, 153); padding: 5px; overflow: auto; font-family: Andale Mono,Lucida Console,Monaco,fixed,monospace; color: rgb(0, 0, 0); background-color: rgb(238, 238, 238); font-size: 12px; line-height: 14px; width: 100%;"}
      var image = ImageView {x: bind monsterXy: bind monsterYvisible: bind visiblityimage: Image {  url: "{__DIR__}resources/monster.png"}transforms: Rotate { pivotX : bind monsterX+25, pivotY : bind monsterY+25, angle: bind rotation }}
    ~~~~

2.  Next, we define the timeline for making the monster move to and fro.
    The to and fro motion is enabled by the "autoReverse: True"
    expression.

    ~~~~
    {style="border: 1px dashed rgb(153, 153, 153); padding: 5px; overflow: auto; font-family: Andale Mono,Lucida Console,Monaco,fixed,monospace; color: rgb(0, 0, 0); background-color: rgb(238, 238, 238); font-size: 12px; line-height: 14px; width: 100%;"}
     var timeline = Timeline { rate: bind animationRate; repeatCount: Timeline.INDEFINITE autoReverse: true keyFrames : [ at (0s) {monsterX => 0;}, at (4s) {monsterX => 440;} ]}
    ~~~~

3.  After this, we write the isDead function . This function pauses the
    timeline we wrote above and rotates the monster by 180 degrees and
    then makes the timeline play from start. It also increases you score
    by 15 points.

    ~~~~
    {style="border: 1px dashed rgb(153, 153, 153); padding: 5px; overflow: auto; font-family: Andale Mono,Lucida Console,Monaco,fixed,monospace; color: rgb(0, 0, 0); background-color: rgb(238, 238, 238); font-size: 12px; line-height: 14px; width: 100%;"}
    public function isDead(){   timeline.pause();   var isDeadTimeline = Timeline {       repeatCount: 1       keyFrames : [           at (0s){rotation => 0},           at (0.2s){rotation => 180;},           KeyFrame {               time: 0.6s               action: function(){                   Main.score+=15;                   rotation = 0;                   timeline.playFromStart();               }           }       ]   };   isDeadTimeline.play();}
    ~~~~

    \

4.  This was most of what was done in this class. You would have noticed
    that we haven't used the attackTimeline and the attack() function. I
    was writing them to enable the monster attack the player also, but i
    haven't finished that part. So, we'll skip them for the while. Now
    we jump to the important part: Collision Detection. Our task is
    gravely simplified by the intersects() function of the Node class.
    It returns true when your node intersects the mentioned rectangle.
    Read the API for details. Here are the snippets from the prevous
    class, tanks.fx:

    ~~~~
    {style="border: 1px dashed rgb(153, 153, 153); padding: 5px; overflow: auto; font-family: Andale Mono,Lucida Console,Monaco,fixed,monospace; color: rgb(0, 0, 0); background-color: rgb(238, 238, 238); font-size: 12px; line-height: 14px; width: 100%;"}
        public function colissionDetect(){    if(monster.intersects(bulletX,bulletY,10,15)){        monster.isDead();    }}
    ~~~~

    \
    We've defined our rectangle with respect to the coordinates of the
    bullet using the bulletX and bulletY variables. Whenever the monster
    intersects this bullet, the monster.isDead() function is triggered.
    Note that we are polling to verify the intersection every 0.1 second
    by playing the colissionTimeline variable:

    ~~~~
    {style="border: 1px dashed rgb(153, 153, 153); padding: 5px; overflow: auto; font-family: Andale Mono,Lucida Console,Monaco,fixed,monospace; color: rgb(0, 0, 0); background-color: rgb(238, 238, 238); font-size: 12px; line-height: 14px; width: 100%;"}
        var colissionTimeline = Timeline {    repeatCount: Timeline.INDEFINITE    keyFrames : [        KeyFrame {            time : 0.1s            action: function(){colissionDetect()}        }    ]}
    ~~~~

    This timeline is played throughout the duration of the game.

So, that's all, we're done with most of the part of the game. The
scoring part is simple, you can figure it out very easily in the Main.fx
file:

~~~~
{style="border: 1px dashed rgb(153, 153, 153); padding: 5px; overflow: auto; font-family: Andale Mono,Lucida Console,Monaco,fixed,monospace; color: rgb(0, 0, 0); background-color: rgb(238, 238, 238); font-size: 12px; line-height: 14px; width: 100%;height: 300px"}
/** Main.fx** Created on Jun 21, 2009, 9:17:55 AM*/package spaceinvadersfx;import javafx.stage.Stage;import javafx.scene.Scene;import javafx.scene.text.Text;import javafx.scene.text.Font;import javafx.scene.media.Media;import javafx.scene.media.MediaPlayer;/*** @author Sagar Jauhari*/public var score = 0;public var lives = 3;public var screenWidth = 500;public var screenHeight = 500;var scoreText = Text { font : Font {     size: 20 } x: screenWidth-40, y: screenHeight-30 content: bind {java.lang.String.valueOf(score)}};var mdeia = MediaPlayer { media : Media {     source: "" }}public function run(){Stage { title: "Space Invaders FX by Sagar Jauhari" width: 500 height: 500 scene: Scene {     content: bind [tank{},scoreText] }}}
~~~~

We defined a variable ScoreText and bound its value to the score
variable which is changed everytime you hit the monster.\
\
More to be done:\

1.  The monster has to be coded to attact the tank also! Right now the
    game is too easy!\
2.  Background music can be played and specific sounds can be added to
    the fire() and isDead() functions.

The sourcecode of the game can be downloaded from
[here.](http://worldofocean.googlepages.com/spaceinvadersfx.rar)\

