## 10주차 ㄷㄷㄷㄷ
제이쿼리를 학습해보았다.
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <p id="action"> </p>
    <script>
        var a = 100;
        var b = 200;
        document.getElementById('action').innerHTML = a + b;
    </script>
</body>
</html>
```



![image](https://github.com/user-attachments/assets/df147929-83c9-4372-afd3-213d8aad3e7e)
***

태양계를 표현하는 코드도 작성 해봤다.
```
<!DOCTYPE html>
<html>

<head>
</head>

<body>
    <h1 id="sun">@</h1>
    <h1 id="earth">O</h1>
    <h1 id="moon">*</h1>
    <script>
        window.onload = function () {
            // 변수를 선언합니다.
            var sun = document.getElementById('sun');
            var earth = document.getElementById('earth');
            var moon = document.getElementById('moon');

            // 문서 객체의 스타일 속성을 변경함.
            sun.style.position = 'absolute';
            earth.style.position = 'absolute';
            moon.style.position = 'absolute';
            sun.style.left = 250 + 'px';
            sun.style.top = 250 + 'px';

            var earthAngle = 0;
            var moonAngle = 0;

            setInterval(function () {
                // 지구의 좌표 계산 (태양 중심으로 회전)
                var earthRadius = 150;  // 지구의 궤도 반경
                var earthLeft = 250 + earthRadius * Math.cos(earthAngle);
                var earthTop = 250 + earthRadius * Math.sin(earthAngle);

                // 달의 좌표 계산 (지구 중심으로 회전)
                var moonRadius = 50;  // 달의 궤도 반경
                var moonLeft = earthLeft + moonRadius * Math.cos(moonAngle);
                var moonTop = earthTop + moonRadius * Math.sin(moonAngle);

                // 지구와 달의 위치 업데이트
                earth.style.left = earthLeft + 'px';
                earth.style.top = earthTop + 'px';
                moon.style.left = moonLeft + 'px';
                moon.style.top = moonTop + 'px';

                // 각도 증가
                earthAngle += 0.02;  // 지구의 회전 속도
                moonAngle += 0.1;    // 달의 회전 속도
            }, 1000 / 60);  // 60fps로 실행
        };
    </script>
</body>

</html>
```
![image](https://github.com/user-attachments/assets/ca4d03ab-e9a1-4373-a25c-65e97db48955)
***
제이쿼리도 사용 해 봤다.
```
<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <title>jQuery</title>

    <script src="https://code.jquery.com/jquery-3.7.1.js" 
        integrity="sha256-eKhayi8LEQwp4NKxN+CfCh+3qOVUtJn3QNZ0TciWLP4=" 
        crossorigin="anonymous">
</script>>
</head>
<body>
    <h1>반갑습니다.</h1>

    <script>
        $(document).ready(function() {
            $('*').css('color', 'red');
        });
    </script>
</body>
</html>
```



![image](https://github.com/user-attachments/assets/ea2941aa-62a6-4b04-9945-d6b61ed5865b)

