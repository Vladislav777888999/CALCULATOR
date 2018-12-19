"# CALCULATOR" 
cыс
import sys
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

        self.label = QLabel(self)
        self.label.setText("Пока все законно")
        self.label.move(40, 30)

        self.int_label1 = QLabel(self)
        self.int_label1.setText("Введите первое число: ")
        self.int_label1.move(10, 60)

        self.int_input1 = QLineEdit(self)
        self.int_input1.move(200, 60)

        self.int_label2 = QLabel(self)
        self.int_label2.setText("Введите второе число: ")
        self.int_label2.move(10, 90)

        self.int_input2 = QLineEdit(self)
        self.int_input2.move(200, 90)

        self.int_label3 = QLabel(self)
        self.int_label3.setText("Введите арифметическое действие: ")
        self.int_label3.move(10, 120)
        
        self.int_input3 = QLineEdit(self)
        self.int_input3.move(200, 120)        
        
        self.LCD_sum = QLCDNumber(self)
        self.LCD_sum.move(20, 180)

        self.LCD_raz = QLCDNumber(self)
        self.LCD_raz.move(50, 180)
