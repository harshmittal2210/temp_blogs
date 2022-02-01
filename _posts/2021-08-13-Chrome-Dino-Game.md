---
date: 2021-08-13T23:48:05.000Z
layout: post
title: Dino Game in Arduino
subtitle: 'The T-Rex Game (Chrome Dino) in Arduino using OLED Display'
description: >-
  Learn to create Dino game in arduino using OLED display.
image: >-
  https://res.cloudinary.com/dog8hn5qv/image/upload/v1641073691/blog/The_T-Rex_Game_Chrome_Dino_in_Arduino_using_OLED_Display_phsamk.png
optimized_image: >-
 https://res.cloudinary.com/dog8hn5qv/image/upload/c_scale,w_380/v1641073691/blog/The_T-Rex_Game_Chrome_Dino_in_Arduino_using_OLED_Display_phsamk.png
category: YouTube
tags:
  - Arduino
  - Game
  - Chrome
  - Dino
  - C++
  - Serial
  - OLED
author: harshmittal
paginate: true
---

Learn to create Dino game in arduino using OLED display.

## Things used in this project 
- [Arduino Mega 2560](https://amzn.to/3eMbmUY)
- [OLED 64x128 Display Module](https://amzn.to/3sOL64B)
- Arduino IDE

## Story 
We all have played the dino game in chrome whenever our internet is not working. I am not so good at playing it though but thought of creating the basic version of the game in Arduino.

![Chrome Dino Game](https://hackster.imgix.net/uploads/attachments/1323159/image_mBCfp5vQuj.png?auto=compress%2Cformat&w=740&h=555&fit=max)

For a complete tutorial you can check out the youtube video:


[![Tutorial YouTube Video](https://img.youtube.com/vi/TcjWpDrWnmM/0.jpg)](https://youtu.be/TcjWpDrWnmM)

Source Code: [Github Link](https://gist.github.com/harshmittal2210/85a47f25eafe6b71ea4f1ce5c46a2465)


## Implementation
Connect the jumper wires according to the image shown below.

(Note: Wire number can be different for your boards, please read the documentation)

![Pin Diagram](https://hackster.imgix.net/uploads/attachments/1323161/capture_sjcXKFDits.JPG?auto=compress%2Cformat&w=740&h=555&fit=max)

Create a new sketchbook in Arduino IDE and select the correct boards and port.

Include the Lib:

```c
// Include
#include <Wire.h>
#include <Adafruit_GFX.h>
#include <Adafruit_SSD1306.h>
```
Note: Remember to install Adafruit Lib in Arduino

Add defines:
```c
// Screen Info
#define SCREEN_WIDTH 128 // OLED display width, in pixels
#define SCREEN_HEIGHT 64 // OLED display height, in pixels
#define OLED_RESET     4 // Reset pin # (or -1 if sharing Arduino reset pin)
#define SCREEN_ADDRESS 0x3C

// Dino Info
#define DINO_WIDTH 25
#define DINO_HEIGHT 26
#define DINO_INIT_X 10
#define DINO_INIT_Y 29

// Line info
#define BASE_LINE_X 0
#define BASE_LINE_Y 54
#define BASE_LINE_X1 127
#define BASE_LINE_Y1 54

// Trees info
#define TREE1_WIDTH 11
#define TREE1_HEIGHT 23
#define TREE2_WIDTH 22
#define TREE2_HEIGHT 23
#define TREE_Y 35

#define JUMP_PIXEL 22 // Max jump in pixel
```

Init display

```c
Adafruit_SSD1306 display(SCREEN_WIDTH, SCREEN_HEIGHT, &Wire, OLED_RESET);
```

Generate a byte array of dino and trees.

You can use the site: [https://javl.github.io/image2cpp/](https://javl.github.io/image2cpp/)

![Double Tree](https://hackster.imgix.net/uploads/attachments/1324364/tree1_2PTuK85jOt.png?auto=compress%2Cformat&w=740&h=555&fit=max)

![Single Tree](https://hackster.imgix.net/uploads/attachments/1324363/tree_DYrRRkiMXu.png?auto=compress%2Cformat&w=740&h=555&fit=max)

![Dino](https://hackster.imgix.net/uploads/attachments/1324361/dino_HI4HteCYmo.png?auto=compress%2Cformat&w=740&h=555&fit=max)


```c
static const unsigned char PROGMEM dino1[]={
  // 'dino', 25x26px
0x00, 0x00, 0x00, 0x00, 0x00, 0x07, 0xfe, 0x00, 0x00, 0x06, 0xff, 0x00, 0x00, 0x0e, 0xff, 0x00, 
0x00, 0x0f, 0xff, 0x00, 0x00, 0x0f, 0xff, 0x00, 0x00, 0x0f, 0xff, 0x00, 0x00, 0x0f, 0xc0, 0x00, 
0x00, 0x0f, 0xfc, 0x00, 0x40, 0x0f, 0xc0, 0x00, 0x40, 0x1f, 0x80, 0x00, 0x40, 0x7f, 0x80, 0x00, 
0x60, 0xff, 0xe0, 0x00, 0x71, 0xff, 0xa0, 0x00, 0x7f, 0xff, 0x80, 0x00, 0x7f, 0xff, 0x80, 0x00, 
0x7f, 0xff, 0x80, 0x00, 0x3f, 0xff, 0x00, 0x00, 0x1f, 0xff, 0x00, 0x00, 0x0f, 0xfe, 0x00, 0x00, 
0x03, 0xfc, 0x00, 0x00, 0x01, 0xdc, 0x00, 0x00, 0x01, 0x8c, 0x00, 0x00, 0x01, 0x8c, 0x00, 0x00, 
0x01, 0x0c, 0x00, 0x00, 0x01, 0x8e, 0x00, 0x00
};

static const unsigned char PROGMEM tree1[]={
  // 'tree1', 11x23px
0x1e, 0x00, 0x1f, 0x00, 0x1f, 0x40, 0x1f, 0xe0, 0x1f, 0xe0, 0xdf, 0xe0, 0xff, 0xe0, 0xff, 0xe0, 
0xff, 0xe0, 0xff, 0xe0, 0xff, 0xe0, 0xff, 0xe0, 0xff, 0xc0, 0xff, 0x00, 0xff, 0x00, 0x7f, 0x00, 
0x1f, 0x00, 0x1f, 0x00, 0x1f, 0x00, 0x1f, 0x00, 0x1f, 0x00, 0x1f, 0x00, 0x1f, 0x00
};

static const unsigned char PROGMEM tree2[]={
  // 'tree2', 22x23px
0x1e, 0x01, 0xe0, 0x1f, 0x03, 0xe0, 0x1f, 0x4f, 0xe8, 0x1f, 0xff, 0xfc, 0x1f, 0xff, 0xfc, 0xdf, 
0xff, 0xfc, 0xff, 0xff, 0xfc, 0xff, 0xff, 0xfc, 0xff, 0xff, 0xfc, 0xff, 0xff, 0xfc, 0xff, 0xff, 
0xfc, 0xff, 0xef, 0xfc, 0xff, 0x83, 0xfc, 0xff, 0x03, 0xfc, 0xff, 0x03, 0xf8, 0x7f, 0x03, 0xe0, 
0x1f, 0x03, 0xe0, 0x1f, 0x03, 0xe0, 0x1f, 0x03, 0xe0, 0x1f, 0x03, 0xe0, 0x1f, 0x03, 0xe0, 0x1f, 
0x03, 0xe0, 0x1f, 0x03, 0xe0
};
```

### setup()
```c
Serial.begin(9600);
// SSD1306_SWITCHCAPVCC = generate display voltage from 3.3V internally
if(!display.begin(SSD1306_SWITCHCAPVCC, SCREEN_ADDRESS)) {
    Serial.println(F("SSD1306 allocation failed"));
    for(;;); // Don't proceed, loop forever
}
// Clear the buffer
display.clearDisplay();
introMessage();
// Run game in loop
while(1){
    if (Serial.available()){
        if(Serial.parseInt()==1){
            play();
        }
    }
}
```

`introMessage()` function will display the game name and further instructions

```c
void introMessage(){
  display.setTextSize(2);             // Draw 2X-scale text
  display.setTextColor(SSD1306_WHITE);
  display.setCursor(10,5);
  display.println("Dino Game");
  display.setTextSize(1);
  display.setCursor(5,45);
  display.println("Enter 1 To Play ");
  display.display();
}
```

`play()` is the main game function. Let's Break it down into smaller pieces for better understanding.

```c
# Initialize everything
int16_t tree_x=127; // End of the screen
int16_t tree1_x=195; // So that second type of tree comes after some time
int tree_type = random(0,2); // Select random type of tree
int tree_type1 = random(0,2);
int16_t dino_y = DINO_INIT_Y; 
int input_command;
int jump=0; // init jump state is 0 i.e on base
int score=0;
```
The rest of the code will be in a `for` loop unless a collision happens:

```c
display.clearDisplay();

if (Serial.available()){ // Check for serial Data
  input_command = Serial.parseInt();
  if(input_command==5){ // Jump
    Serial.println("Jump");
    if(jump==0) jump=1;
  }
}
```
Change Jump status:

```c
if(jump==1){ // Going UP
  dino_y--;
  if(dino_y== (DINO_INIT_Y-JUMP_PIXEL)){
    jump=2;
    score++;
  }
}
else if(jump==2){ // Comming down
  dino_y++;
  if(dino_y== DINO_INIT_Y){
   jump=0;
  }
}
```

Check for collision:
```c
if(tree_x<= (DINO_INIT_X+DINO_WIDTH) && tree_x>= (DINO_INIT_X+(DINO_WIDTH/2))){
//      Serial.println("Might be Collision Happend");
  if(dino_y>=(DINO_INIT_Y-3)){
    // Collision Happened
    Serial.println("Collision Happend");
    break;
  }
}
if(tree1_x<= (DINO_INIT_X+DINO_WIDTH) && tree1_x>= (DINO_INIT_X+(DINO_WIDTH/2))){
//      Serial.println("Might be Collision Happend");
  if(dino_y>=(DINO_INIT_Y-3)){
    // Collision Happened
    Serial.println("Collision Happend");
    break;
  }
}
```

Render the scene:

```c
displayScore(score); // Live Score
moveTree(&tree_x,tree_type);// Move tree 1
moveTree(&tree1_x,tree_type1); // Move tree 2
moveDino(&dino_y); // Move dino
display.drawLine(0,54,127,54, SSD1306_WHITE); // Base line
```

Move trees:
```c
tree_x--;
tree1_x--;
if(tree_x==0) {
  tree_x = 127;
  tree_type = random(0,1);
}
if(tree1_x==0) {
  tree1_x = 195;
  tree_type1 = random(0,1);
}
```

Display everything:
```c
display.display();
```

Once collision happens:
```c
Serial.println("Game Over");
gameOver(score);
```

Move dino and tree:
```c
// Move dino function
void moveDino(int16_t *y, int type=0){
    display.drawBitmap(DINO_INIT_X, *y, dino1, DINO_WIDTH, DINO_HEIGHT, SSD1306_WHITE);
}
// Move tree function
void moveTree(int16_t *x, int type=0){
  if(type==0){
    display.drawBitmap(*x, TREE_Y, tree1, TREE1_WIDTH, TREE1_HEIGHT, SSD1306_WHITE);
  }
  else if(type==1){
    display.drawBitmap(*x, TREE_Y, tree2, TREE2_WIDTH, TREE2_HEIGHT, SSD1306_WHITE);
  }
}
```

`gameOver()`:

```c
// Game over display with score
void gameOver(int score=0){
  display.clearDisplay();
  display.setTextSize(2);             // Draw 2X-scale text
  display.setTextColor(SSD1306_WHITE);
  display.setCursor(10,5);
  display.println("Game Over");
  display.setTextSize(1);
  display.setCursor(10,30);
  display.print("Score: ");
  display.print(score);
  display.setCursor(1,45);
  display.println("Enter 1 To Play Again");
  display.display();
}
```

This concludes this tutorial on creating a very basic game using Arduino and OLED. For the demo check out the video:


[![Tutorial YouTube Video](https://img.youtube.com/vi/TcjWpDrWnmM/0.jpg)](https://youtu.be/TcjWpDrWnmM)


Hope you liked it!!


To buy the products visit:

OLED Display: [https://amzn.to/3B7MkK9](https://amzn.to/3B7MkK9)

Arduino Mega: https://amzn.to/36EwI2U

ESP-32: https://amzn.to/3xMRAAL

Jumper Wire: https://amzn.to/3z0Jox1

Bread Board: https://amzn.to/2Ue4Y2l




