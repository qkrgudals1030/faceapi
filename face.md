#https://cafe.naver.com/newgraphics/91 를 참고하여
#사람의 얼굴에 눈썹을 만들거나 변형하고,
#입술에 화장을 할 수 있는 프로그램을 만드시오.


```
   
let img, parts;
let options = {withLandmarks: true, withDescriptors: false};

function preload() {
  img = loadImage('face.png');
}

function setup() {
  createCanvas(img.width*2, img.height);
  faceapi = ml5.faceApi(options, modelReady);
  background(255);
  image(img, img.width, 0);    
}

function modelReady() {
  faceapi.detectSingle(img, gotResults);
}

function gotResults(err, results) {
  if (err) {
    console.error(err);
    return;
  }
  console.log(results);
  parts = results.parts;
  noFill();
  stroke(0, 0, 255);
  strokeWeight(3);
  drawFace();
}

function drawFace() {
  stroke(255, 0, 255);

  //입술그리기
  beginShape();
  for(let i=0; i<parts.mouth.length; i++){
    vertex(parts.mouth[i]._x, parts.mouth[i]._y);
    fill(255,0,0);
  }
  vertex(parts.mouth[0]._x, parts.mouth[0]._y);
  fill(255,0,0);
  endShape();

  //코 그리기    
  beginShape();
  for(let i=0; i<parts.nose.length; i++){
    vertex(parts.nose[i]._x, parts.nose[i]._y);
  }
  fill(0,255,0);
  endShape();

  //눈 그리기
  beginShape();
  for(let i=0; i<parts.leftEye.length; i++){
    vertex(parts.leftEye[i]._x, parts.leftEye[i]._y);
  }
  vertex(parts.leftEye[0]._x, parts.leftEye[0]._y);
  fill(0);
  endShape();

  beginShape();
  for(let i=0; i<parts.rightEye.length; i++){
    vertex(parts.rightEye[i]._x, parts.rightEye[i]._y);
  }
  vertex(parts.rightEye[0]._x, parts.rightEye[0]._y);
  fill(255);
  endShape();

  //눈썹 그리기    
  beginShape();
  for(let i=0; i<parts.leftEyeBrow.length; i++){
    vertex(parts.leftEyeBrow[i]._x, parts.leftEyeBrow[i]._y);
  }
  fill(0,0,255);
  endShape();

  beginShape();
  for(let i=0; i<parts.rightEyeBrow.length; i++){
    vertex(parts.rightEyeBrow[i]._x, parts.rightEyeBrow[i]._y);
  }
  fill(100,100,0);
  endShape();
}

```
