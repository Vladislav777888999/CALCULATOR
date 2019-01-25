"""# CALCULATOR"""
import sys
import math
from PyQt5.QtWidgets import QApplication, QWidget, QPushButton
from PyQt5.QtWidgets import QLCDNumber, QLabel, QLineEdit


class Example(QWidget):
    def __init__(self):
        super().__init__()
        self.initUI()

    def initUI(self):
        self.setGeometry(300, 300, 350, 220)
        self.setWindowTitle('Калькулятор')

        self.btn = QPushButton('Рассчитать', self)
        self.btn.resize(self.btn.sizeHint())
        self.btn.move(100, 150)
        self.btn.clicked.connect(self.hello)

        self.btn = QPushButton('Сбросить', self)
        self.btn.resize(self.btn.sizeHint())
        self.btn.move(180, 150)
        self.btn.clicked.connect(self.nul)

        self.int_label1 = QLabel(self)
        self.int_label1.setText("Введите первое число: ")
        self.int_label1.move(10, 60)

        self.int_input1 = QLineEdit(self)
        self.int_input1.move(200, 60)

        self.int_label2 = QLabel(self)
        self.int_label2.setText("Введите арифметическое действие: ")
        self.int_label2.move(10, 90)

        self.int_input2 = QLineEdit(self)
        self.int_input2.move(200, 90)

        self.int_label3 = QLabel(self)
        self.int_label3.setText("Введите второе число: ")
        self.int_label3.move(10, 120)

        self.int_input3 = QLineEdit(self)
        self.int_input3.move(200, 120)

        self.LCD_ans = QLCDNumber(self)
        self.LCD_ans.move(140, 180)

    def hello(self):
        int1 = self.int_input1.text()
        int2 = self.int_input2.text()
        if int1 == 'ФОКУС':
            self.LCD_ans.display(int(int2) - 250)
        else:
            if int2 == '*/':
                if int(int1) > 0:
                    self.LCD_ans.display(math.sqrt(int(int1)))
                else:
                    self.LCD_ans.display('error')
            elif int2 == '**':
                self.LCD_ans.display((int(int1) ** 2))
            elif int2 == '***':
                self.LCD_ans.display((int(int1) ** 3))
            elif int2 == '!':
                self.LCD_ans.display(math.factorial(int(int1)))
            else:
                int3 = self.int_input3.text()
                if int2 == '/':
                    if int(int3) == 0:
                        self.LCD_ans.display('error')
                    else:
                        self.LCD_ans.display(int(int1) / int(int3))
                elif int2 == '/n':
                    self.LCD_ans.display((int(int1) + int(int3)) / 2)
                elif int2 == '/g':
                    self.LCD_ans.display(math.sqrt(int(int1) * int(int3)))                
                elif int2 == '/d':
                    a = int(int1)
                    b = int(int3)
                    while a != 0 and b != 0:
                        if a > b:
                            a %= b
                        else:
                            b %= a
                    self.LCD_ans.display(a + b)
                elif int2 == '/k':
                    a = int(int1)
                    b = int(int3)
                    if a > b:
                        greater = a
                    else:
                        greater = b
                    while(True):
                        if((greater % a == 0) and (greater % b == 0)):
                            lcm = greater
                            break
                        greater += 1
                    self.LCD_ans.display(lcm)                    
                elif int2 == '+':
                    self.LCD_ans.display(int(int1) + int(int3))
                elif int2 == '-':
                    self.LCD_ans.display(int(int1) - int(int3))
                elif int3 == '*':
                    self.LCD_ans.display(int(int1) * int(int3))

    def nul(self):
        self.LCD_ans.display('0')


if __name__ == '__main__':
    app = QApplication(sys.argv)
    ex = Example()
    ex.show()
    sys.exit(app.exec())
