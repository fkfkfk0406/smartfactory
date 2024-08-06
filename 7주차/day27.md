길고 짧은 휴가가 끝났다...
다녀오니 골골대는 몸뚱이 밖에 안남았다. 컨디션 조절을 잘하자
***
```
![화면 캡처 2024-08-06 094951](https://github.com/user-attachments/assets/c98ab2b8-702c-4369-8773-de93d1e42496)



뇌풀기 윈폼 복습

namespace P179
{
    public partial class Form1 : Form
    {
        int sajin = 1;
        int sajin_max = 5;
        public Form1()
        {
            InitializeComponent();
        }
        private void timer1_Tick(object sender, EventArgs e)
        {
            pictureBox1.Image = Image.FromFile(System.Environment.CurrentDirectory + "/1/" + sajin + ".png");
                sajin++;

            if (sajin > sajin_max)
                sajin = 1;
        }
    }
}
```
```
트랙바를 이용한 RGB 표현
namespace WinFormsApp8
{
    public partial class Form1 : Form
    {
        public Form1()
        {
            InitializeComponent();
        }

        private void Form1_Load(object sender, EventArgs e)
        {
            trackBarR.Value = 0;
            trackBarG.Value = 0;
            trackBarB.Value = 0;

            UpdateColor();
        }
        private void trackBarR_Scroll(object sender, EventArgs e)
        {
            UpdateColor();
        }
        private void trackBarG_Scroll(object sender, EventArgs e)
        {
            UpdateColor();
        }
        private void trackBarB_Scroll(object sender, EventArgs e)
        {
            UpdateColor();
        }
        //사용자 정의 함수
        private void UpdateColor()
        {
            int red = trackBarR.Value;
            int green = trackBarG.Value;
            int blue = trackBarB.Value;
            pictureBox1.BackColor = Color.FromArgb(red, green, blue);
        }
    }
}
```
***
![image](https://github.com/user-attachments/assets/b4d80498-31c9-4d65-b06c-bc563e1a5806)



SQLDEVELOPER 로 실습을 해보았다.
***
![image](https://github.com/user-attachments/assets/efedafba-c4df-4fc0-8544-cfcdb63e50ef)



STARUML을 활용해서 실습을 해봤다.
***

