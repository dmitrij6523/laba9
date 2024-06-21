Лабораторная работа№9 Библиотека Requests, исследование HTTP методов.

## Код сервера:

from flask import Flask, request, jsonify

app = Flask(__name__)

# Пример данных, которые могут быть хранимы на сервере
students = [
    {"id": 1, "name": "Иванов Иван", "age": 20, "major": "Информатика"},
    {"id": 2, "name": "Петров Петр", "age": 21, "major": "Математика"},
    {"id": 3, "name": "Сидорова Анна", "age": 19, "major": "Физика"}
]

# Метод GET для получения списка всех студентов


@app.route('/students', methods=['GET'])
def get_students():
    return jsonify(students)

# Метод GET для получения данных конкретного студента по его идентификатору


@app.route('/students/<int:id>', methods=['GET'])
def get_student(id):
    student = next((s for s in students if s["id"] == id), None)
    if student:
        return jsonify(student)
    else:
        return jsonify({"message": "Студент с указанным идентификатором не найден"}), 404

# Метод POST для добавления нового студента


@app.route('/students', methods=['POST'])
def add_student():
    new_student = request.json
    students.append(new_student)
    return jsonify({"message": "Студент успешно добавлен", "student": new_student}), 201

# Метод PUT для обновления данных студента


@app.route('/students/<int:id>', methods=['PUT'])
def update_student(id):
    student = next((s for s in students if s["id"] == id), None)
    if student:
        data = request.json
        student.update(data)
        return jsonify({"message": "Данные студента успешно обновлены", "student": student})
    else:
        return jsonify({"message": "Студент с указанным идентификатором не найден"}), 404

# Метод DELETE для удаления студента по его идентификатору


@app.route('/students/<int:id>', methods=['DELETE'])
def delete_student(id):
    global students
    students = [s for s in students if s["id"] != id]
    return jsonify({"message": "Студент успешно удален"})


if __name__ == '__main__':
    app.run(port=80, host="0.0.0.0", debug=False)

# Пример данных, которые могут быть хранимы на сервере
students = [
    {"id": 1, "name": "Иванов Иван", "age": 20, "major": "Информатика"},
    {"id": 2, "name": "Петров Петр", "age": 21, "major": "Математика"},
    {"id": 3, "name": "Сидорова Анна", "age": 19, "major": "Физика"}
]

# Метод GET для получения списка всех студентов


@app.route('/students', methods=['GET'])
def get_students():
    return jsonify(students)

# Метод GET для получения данных конкретного студента по его идентификатору


@app.route('/students/<int:id>', methods=['GET'])
def get_student(id):
    student = next((s for s in students if s["id"] == id), None)
    if student:
        return jsonify(student)
    else:
        return jsonify({"message": "Студент с указанным идентификатором не найден"}), 404

# Метод POST для добавления нового студента


@app.route('/students', methods=['POST'])
def add_student():
    new_student = request.json
    students.append(new_student)
    return jsonify({"message": "Студент успешно добавлен", "student": new_student}), 201

# Метод PUT для обновления данных студента


@app.route('/students/<int:id>', methods=['PUT'])
def update_student(id):
    student = next((s for s in students if s["id"] == id), None)
    if student:
        data = request.json
        student.update(data)
        return jsonify({"message": "Данные студента успешно обновлены", "student": student})
    else:
        return jsonify({"message": "Студент с указанным идентификатором не найден"}), 404

# Метод DELETE для удаления студента по его идентификатору


@app.route('/students/<int:id>', methods=['DELETE'])
def delete_student(id):
    global students
    students = [s for s in students if s["id"] != id]
    return jsonify({"message": "Студент успешно удален"})


if __name__ == '__main__':
    app.run(port=80, host="0.0.0.0", debug=False)
# Пример данных, которые могут быть хранимы на сервере
students = [
    {"id": 1, "name": "Иванов Иван", "age": 20, "major": "Информатика"},
    {"id": 2, "name": "Петров Петр", "age": 21, "major": "Математика"},
    {"id": 3, "name": "Сидорова Анна", "age": 19, "major": "Физика"}
]

# Метод GET для получения списка всех студентов


@app.route('/students', methods=['GET'])
def get_students():
    return jsonify(students)

# Метод GET для получения данных конкретного студента по его идентификатору


@app.route('/students/<int:id>', methods=['GET'])
def get_student(id):
    student = next((s for s in students if s["id"] == id), None)
    if student:
        return jsonify(student)
    else:
        return jsonify({"message": "Студент с указанным идентификатором не найден"}), 404

# Метод POST для добавления нового студента


@app.route('/students', methods=['POST'])
def add_student():
    new_student = request.json
    students.append(new_student)
    return jsonify({"message": "Студент успешно добавлен", "student": new_student}), 201

# Метод PUT для обновления данных студента


@app.route('/students/<int:id>', methods=['PUT'])
def update_student(id):
    student = next((s for s in students if s["id"] == id), None)
    if student:
        data = request.json
        student.update(data)
        return jsonify({"message": "Данные студента успешно обновлены", "student": student})
    else:
        return jsonify({"message": "Студент с указанным идентификатором не найден"}), 404

# Метод DELETE для удаления студента по его идентификатору


@app.route('/students/<int:id>', methods=['DELETE'])
def delete_student(id):
    global students
    students = [s for s in students if s["id"] != id]
    return jsonify({"message": "Студент успешно удален"})


if __name__ == '__main__':
    app.run(port=80, host="0.0.0.0", debug=False)

Клиент, в папке client, файл main.py.

Для импорта библиотеки создайте виртуальное окружение python, установите библиотеку через pip, и выполните импорт в коде: import requests.

## Задание №1 Метод GET
Данные
Запустите серверный код он будет доступен по 127.0.0.1:80, данный сервер реализует основные методы HTTP, а именно: GET, POST, PUT, DELETE, ресурс выдает информацию о студентах по слагу /students с методом GET. При передачи дополнительного пути к примеру "/1", передасться информация о 1 студенте.

Для того чтобы сформировать get запрос в библиотеки requests, используйте:

response = requests.get(url)
Для чтения ответа используйте:

response.json()
Задача
Используя библиотеку requests, реализуйте 2 функции выполняющий GET запрос, одна функция должна возвращать список студентов, вторая функция должна принимать параметр “номер студента” и возвращать информацию о конкретном студенте.

## Задание №2 Метод POST
Данные
На сервере реализован прием новой информации о студентах, для этого вам необходимо сформировать POST запрос, и передать в него json код с иформацией о новом студенте.

Для формирования Post запроса вы можете использовать:

response = requests.post(url, json=student_data)
Формат строки json для добавления нового студента:

{"id": 4, "name": "Новый Студент", "age": 22, "major": "Биология"}
Если вы успешно отправите POST запрос то в ответ на него вы получите сообщение об успешном добавление:

{'message': 'Студент успешно добавлен', 'student': {'age': 22, 'id': 4, 'major': 'Биология', 'name': 'Новый Студент'}}
Задача
Используя библиотеку requests, реализуйте функцию принимающую в качестве параметра информацию о новом студенте и добавлющую ее на серве, функция должна возвращать ответ от сервера.

## Задача №3. Метод PUT
Данные
На сервере реализован метод PUT, для обновления инфомации о студенте, для этого необходимо с этим методом передать параметры в таком формате:

updated_student_data = {
        "name": "Новый Студент", "age": 23, "major": "Химия"}
Чтобы обновить инфомацию нужно указать конкретного студента, для этого вам нужно укзать в url id студента как вы это делали в 1 задачи students/1/
Чтобы передать данные методом PUT на сервер используйте:

response = requests.put(url, json=updated_data)
Формат для обновления данных:

{"name": "Новый Студент", "age": 23, "major": "Химия"}
Ожидаемый ответ:

{'message': 'Данные студента успешно обновлены', 'student': {'age': 23, 'id': 4, 'major': 'Химия', 'name': 'Новый Студент'}}
Задача
Реализуйте функцию которая будет принимать 2 параметра, первый = id студента, второй обновляемая инфомация. Функция должна возвращать строку ответа от сервера указанную в ожидаемом ответе.

## Задача №4. Метод DELETE
На сервере реализован функционал удаления информации о студенте, с помощью метода Delete, что бы это сделать выполните http запрос с методом DELETE и укажите url с id студента как вы это делали в задачи 1.

Вызов метода можно выполнить:

response = requests.delete(url)
Ожидаемы ответ от сервера:

{'message': 'Студент успешно удален'}
Задача
Реализуйте функцию которая будет удалить информацию о студенте по id студента переданному в качестве параметра функции. Функция должна возвращать ответ от сервера.

## Задача №5. Захват HTTP трафика
Запустите Wireshark для looback интерфейса и захватите трафик который генерирует написанный вами клиент, для данного сервера, в дампе трафика ожидаемы все методы реализованные вами:

![image](https://github.com/dmitrij6523/laba9/assets/158767012/592bdd2f-472d-43c4-be7d-b9dabce33093)


Расскрывая информацию о каждом http сообщение опишите что просиходит в данном дампе, какие есть заголовки и параметры у протокола http в запросе, какие в ответе. В каком формате передаються данные между сервером и клиентом? Почему кирилица отображаеться не коректно в дампе?
