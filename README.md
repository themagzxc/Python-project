# Python-project
# Рисование одного элементе змейки
def draw_element(x, y):
    canvas.create_oval((x + 1) * 25, (y + 1) * 25, (x + 2) * 25, (y + 2) * 25, fill='gold')

# Рисование змейки
def draw_snake():
    global table_x, table_y
    i = 0
    while i < len(table_x):
        draw_element(table_x[i], table_y[1])
        i +=1


# Изменение напрвления змейки с клавы
def left(event):
    global vx, vy
    vx = -1
    vy = 0


def right(event):
    global vx, vy
    vx = 1
    vy = 0


def up(event):
    global vx, vy
    vx = 0
    vy = -1


def down(event):
    global vx, vy
    vx = 0
    vy = 1


# Подключение библиотек
from tkinter import *
import time
import random

# Назначение главного окна
root = Tk()
# Настройка окна
root.title('Змейка')
root.geometry('800x550')
root.resizable(width=False, height=False)
root['bg'] = 'white'

# Создание окна для рисования
canvas = Canvas(root, bg='brown', width=800, height=550)
canvas.pack()


# Координаты элементов змейки
table_x = [11, 12, 13, 14]
table_y = [3, 3, 3, 3]

# Направление змейки с клавы
vx = -1
vy = 0

# События bind
root.bind('<Left>', left)
root.bind('<Right>', right)
root.bind('<Up>', up)
root.bind('<Down>', down)

win = True

# Запуск игры
while win:
    table_x = [table_x[0] + vx] + table_x  # изменяем координаты
    table_y = [table_y[0] + vy] + table_y

    table_x.pop(-1) # Удаление посл элемента списка
    table_y.pop(-1)

    draw_snake() #Ричуем змейку
    canvas.update() #Обновляем окно
    time.sleep(0.2) # Скорость змейки
    canvas.delete('all') # Очистка экрана
41# Запуск окна
root.mainloop()
