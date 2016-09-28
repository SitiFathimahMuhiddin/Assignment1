float easing = 0.05;
float x = mouseX;
float y = mouseY;
float ix = width - mouseX; // Inverse X
float iy = height - mouseY; // Inverse Y
boolean drawT = false;
int dragX, dragY, moveX, moveY;
int gray = 0;

void setup() {
  size(640, 360); 
  stroke(0);
  cursor();
  loop();
}

void draw() { 
  background(gray);

  float targetX = mouseX;
  float dx = targetX - x;
  x += dx * easing;
  
  float targetY = mouseY;
  float dy = targetY - y;
  y += dy * easing;
  
 fill(255, 150);
  ellipse(x, height/2, y, y);
  fill(0, 159);
  ellipse(ix, height/2, iy, iy);

  
  ellipse(x, y, 66, 66);
    if (mousePressed == true) {
    if (mouseButton == LEFT) {
      fill(0); // Black
    } else if (mouseButton == RIGHT) { 
      fill(255); // White
    }
  } else {
    fill(126); // Gray
  }
  ellipse(mouseX+20, mouseY+50, 33, 33); // Middle circle
  ellipse(mouseX-20, mouseY-84, 33, 33); // Bottom circle
  
  if (mousePressed == true) {
    cursor(HAND); // Draw cursor as hand
  } else {
    cursor(CROSS);
  }
  line(mouseX, 0, mouseX, height);
  line(0, mouseY, width, mouseY);  
  
  if (mousePressed == true) {
    cursor();
  }
    
  if (drawT == true) { 
      rect(25, y, 50, 30);
    if (mousePressed == true) {
    if (mouseButton == LEFT) {
      fill(0); // Black
    } else if (mouseButton == RIGHT) { 
      fill(255); // White
    }
  } else {
    fill(126); // Gray
  }
    rect(20, 20, 60, 20);
    rect(39, 40, 22, 45);
  }
  
    fill(0); 
  ellipse(dragX, dragY, 33, 33); // Black circle
  fill(153);
  ellipse(moveX, moveY, 33, 33); // Gray circle
  
  if ((mouseX <= 590) && (mouseY <= 310)) {
    rect(0, 0, 50, 50); // Upper-left
  } else if ((mouseX <= 590) && (mouseY > 310)) {
    rect(0, 310, 50, 50); // Lower-left
  } else if ((mouseX > 590) && (mouseY <= 310)) {
    rect(590, 0, 50, 50); // Upper-right
  } else {
    rect(590, 310, 50, 50); // Lower-righT
  }
}


void keyPressed() {
  if ((key == 'T') || (key == 't')) {
    drawT = true;
    gray += 40;
  }
}

void keyReleased() {
  drawT = false;
}

void mousePressed() {
  rect(50, 50, mouseX, mouseY);
  ellipse(mouseY, mouseY, 50, 50);
  gray += 20;
}

void mouseMoved() { // Move gray circle
  moveX = mouseX;
  moveY = mouseY;
  gray += 60;
}

void mouseDragged() { // Move black circle
  dragX = mouseX;
  dragY = mouseY;
  gray += 100;
}
