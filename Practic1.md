# Практическая работа №1
Студент: Бичуцкий Василий Алексеевич.
Группа: ИКБО-62-23

---

## Задание 1

Вывести отсортированный в алфавитном порядке список имен пользователей в файле passwd

![Задание 1. Скриншот выполнения](prac1.png)

## Задание 2

Вывести данные /etc/protocols в отформатированном и отсортированном порядке для 5 наибольших портов, как показано в примере ниже:

![Задание 2. Скриншот выполнения](Задание%202.png)

## Задание 3

Написать программу banner для вывода текстов, как в следующем примере (размер баннера должен меняться!

```python
letter = input()
letter_len = len(letter)
print("+-" + "-" * letter_len + "-+")
print("| " + letter + " |")
print("+-" + "-" * letter_len + "-+")
```

![Задание 3. Скриншот выполнения](Задание%203.png)

## Задание 4

Написать программу для вывода всех индентификаторов по (правилам C/C++ или Java) в файле (без повторений).

```bash
#!/bin/bash

grep -o -E '\b[_a-zA-Z][_a-zA-Z0-9]*\b' "$1" | sort -u | tr '\n' ' '

echo
```

![Задание 4. Скриншот выполнения](Задание%204.png)

## Задание 5

Написать программу для регистрации пользовательской команды (правильные права доступа и копирование в /usr/local/bin).

```bash
#!/bin/bash 

d="/usr/local/bin/$(basename "$file" .py)" 
file=$1 

if [ ! -f $file ]; then 
    echo "File $file not found" 
    exit 1 
fi 

cp $file $d 
chmod 755 $d 
```

![Задание 5. Скриншот выполнения](Задание%205.png)

## Задание 6

Написать программу для проверки наличия комментария в первой строке файлов с расширением c, js и py.

```bash
#!/bin/bash 

for file in *.c *.js *.py; do 
    line=$(head -n 1 "$file") 
    if [[ $line == "#"* || $line == "//"* || $line == "/*"* ]]; then 
        echo "$file: first line is comment" 
    else 
        echo "$file: first line IN NOT comment" 
    fi 
done
```

![Задание 6. Скриншот выполнения](Задание%206.png)

## Задание 7

Написать программу для нахождения файлов-дубликатов (имеющих 1 или более копий содержимого) по заданному пути (и подкаталогам).

```bash
#!/bin/bash 

declare -A hashes 

find_dublicates(){ 
    local dir=$1 

    for file in "$dir"/*; do 
        if [[ -f $file ]]; then 
            hash=$(md5sum $file | awk '{print $1}') 
            if [[ -n ${hashes[$hash]} ]]; then 
                echo "найдены дубликаты по содержанию:" 
                echo "${hashes[$hash]}" 
                echo "$file" 
                echo "          " 
            else 
                hashes[$hash]=$file 
            fi 
        elif [[ -d $file ]]; then 
            fund_dublicates $file 
        fi 
     done 
} 

find_dublicates "."
```

![Задание 7. Скриншот выполнения](Задание%207.png)