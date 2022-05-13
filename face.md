# 그래픽스 팀과제 
## faceApi를 이용한 미용 프로그램의 구현
### 조원: 박형민, 김준영, 손정우 
---

### 코드
```javascript
   
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
---
### 구현결과
![image](https://user-images.githubusercontent.com/50895124/168228113-82b9b435-b771-428c-8854-4c6beabcdb52.png)

---
### 소감
아직 전체적인 코드를 이해하지 못하였지만 최대한 팀원들과 토의하면서 서로 이해한 부분에대해서 설명하고 가르쳐 주는식으로 과제를 진행하였습니다. 사실 저희가 원한건 입술만 칠하는 것이였는데 아직 저희 능력이 부족해서 그거까지 구현을 하지 못하였습니다. 하지만 이번 팀과제를 하면서 기술이 좋아졌다고 생각하였고 코드를 수정해 보면서 그래픽스라는 것에 대해 흥미가 더 생길 수 있는 계기가 되었던것 같습니다. 지금보다더 열심히 수업에 참여 및 개인 공부를 통하여 그래픽스를 자유롭게 다룰 수 있게 되어 그래픽스 작품을 만들 수 있게 되면 좋을 것 같습니다. 그래픽스 화이팅!!!!!!!!!!!!!!!!




