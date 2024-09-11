![image](https://github.com/user-attachments/assets/04d2f612-9c45-4707-87b2-8487ae23fbb5)![image](https://github.com/user-attachments/assets/ec7bd7f9-f6d2-4078-ac38-e90306beed98)## 오늘도 아두이노로 실습을 했다.
![image](https://github.com/user-attachments/assets/ec3d2189-6cb8-4e47-930c-3a207cf5cb98)



이게 가속도(중력센서) 인데
이걸로 실습을 해봤다~~



![image](https://github.com/user-attachments/assets/646e0e8d-1825-44d0-a960-75c06b643e79)



흔들흔들 흔들면 값이 바뀐다,,!
```
#include "SparkFunLIS3DH.h"
#include "Wire.h"
#include "SPI.h"

LIS3DH myIMU; //Default constructor is I2C, addr 0x19.

void setup() {
  Serial.begin(9600);
  delay(1000);
  //Serial.println("Processor came out of reset.\n");
  myIMU.begin();
}
void loop()
{
  //Get all parameters
  //Serial.print("\nAccelerometer:\n");
  Serial.print(" X = ");
  Serial.print(myIMU.readFloatAccelX(), 4);
  Serial.print(" Y = ");
  Serial.print(myIMU.readFloatAccelY(), 4);
  Serial.print(" Z = ");
  Serial.println(myIMU.readFloatAccelZ(), 4);
  delay(40);    // f = 1/40 x 1000 = 약 25Hz
}
```
![image](https://github.com/user-attachments/assets/544f7ac9-0514-459a-9bbb-f10f40c36d60)



코드를 수정해서 흔들흔들하면 그래프가 바뀐다.
***
![image](https://github.com/user-attachments/assets/9c3d4f1a-c53f-4073-bd7f-6be6d100447b)




![image](https://github.com/user-attachments/assets/ee7bbdb5-1a3f-4435-87e2-6717a1ebe171)


온습도 센서를 연결해서 값을 확인해보기도 했따.
