# blue-vs-red---space-and-aliens-code-for-exam
int shipX = 250;//variable - x position ship
int shotX = 250;// variable - x position shot
int shotY = 480;//variable - y position shot
int enemyX = 475;//variable - x position enemy
int enemy2X = 425;//variable - x position enemy 2 
//boolean enemyInvisible = false; //if- true false - enemy is visible
//boolean enemy2Invisible = true;// if true false - enemy 2 is visible
boolean shotInvisible = true;// if true - conditions - invisible shot
String enemyDir = "Left";//string, comparisons, moving left enemy 1
String enemy2Dir = "Left";//string, comparisons, moving left enemy 2
int enemyCount = 2;//variable counter with 2 enemies

void setup() {
  size(500,500);
  background(0);
}
 
void keyPressed() { //ship move speed
  if (keyCode == LEFT) {
    shipX-=20;
  }
  else if (keyCode == RIGHT) {
    shipX+=20;
  }
  else if (keyCode== ' ') {//shot fired
    shotInvisible = false;
    shotX = shipX;
    shotY = 450;
  }
  
  
}//close key pressed
 
void draw() {
  background(0);
  fill(255,0,100);
  triangle(shipX-20,490,shipX+20,490,shipX,460);//ship place and size
  if (shotInvisible) {// shot is invisible at the beginning with its characteristics
    fill(0,0,255,0);
    noStroke();
    if (shotY <= 20){//if shot get a bove 20(ship size) it is still invisble---this is for the beginning
     shotInvisible = true;
   }
  }
 else {
   fill(0,0,255,255);//change collor to blue as it reaches the top
   noStroke();
  }
  ellipse(shotX, shotY, 20, 20);//Shot size and position
  shotY -= 15; //speed of shot
  fill(255,0,0);//color of shot
  triangle(enemyX-20, 55, enemyX+20, 55, enemyX, 35);//enemy creation size and placement
  triangle(enemy2X-20, 55, enemy2X+20, 55, enemy2X, 35);
  if (enemyDir == "Left") {//if enemy goes left
    enemyX -= 5;//speed to go left
    if (enemyX <= 25) {// if enemy is at less that 25
      enemyDir = "Right";//go to the right
    }
  }
  else if (enemyDir == "Right") {
    enemyX += 5;
    if (enemyX >= 475) {
      enemyDir = "Left";
    }
  }
  if (enemy2Dir == "Left") {//same with enemy two
    enemy2X -= 5;
    if (enemy2X <= 25) {
      enemy2Dir = "Right";
    }
  }
  else if (enemy2Dir == "Right") {
    enemy2X += 5;
    if (enemy2X >= 475) {
      enemy2Dir = "Left";
    }
  }//else if enm 2 dir right
  if (shotInvisible == false && shotY >= 45 && shotY <= 55 && shotX >= enemyX-20 && shotX <= enemyX+20) {
    enemyX = 100000000;//shot is invisible in the marked area, marking the area fothe shot nad the ship as they hit, marker down
    enemyCount -= 1;
  }//close if invisible
  if (shotInvisible == false && shotY >= 45 && shotY <= 55 && shotX >= enemy2X-20 && shotX <= enemy2X+20) {
    enemy2X = 100000000;
    enemyCount -= 1;
  }//close shot ivisible
  if (enemyCount == 0) {//when count gets to 0
    background(0);//backgorund transparent
    textSize(100);//size of leters
    textAlign(CENTER);//align text to center
    fill(0, 102, 153);//color of tezt
    text("You Win", width/2, height/2);//text on the center of the screen
    
    textSize(50);
    textAlign(CENTER);
    fill(0, 102, 153);
    text("---GAME--OVER---", width/2, 105);
    
    textSize(30);
    textAlign(CENTER);
    fill(0, 102, 153);
    text("press ENTER to play", width/2, 450);
    
    if (keyCode == ENTER) {
      
      background(0);
      shotX = 250;// variable - x position shot
      shotY = 480;//variable - y position shot
      enemyX = 475;//variable - x position enemy
      enemy2X = 425;
      shotInvisible = true;// if true - conditions - invisible shot
      enemyDir = "Left";//string, comparisons, moving left enemy 1
      enemy2Dir = "Left";//string, comparisons, moving left enemy 2
      enemyCount = 2;

    /*
    int shipX = 250;//variable - x position ship
int shotX = 250;// variable - x position shot
int shotY = 480;//variable - y position shot
int enemyX = 475;//variable - x position enemy
int enemy2X = 425;//variable - x position enemy 2 
//boolean enemyInvisible = false; //if- true false - enemy is visible
//boolean enemy2Invisible = true;// if true false - enemy 2 is visible
boolean shotInvisible = true;// if true - conditions - invisible shot
String enemyDir = "Left";//string, comparisons, moving left enemy 1
String enemy2Dir = "Left";//string, comparisons, moving left enemy 2
int enemyCount = 2;//variable counter with 2 enemies
*/
    }
    
  }//close enemy count
    
  
  
}//close void draw
