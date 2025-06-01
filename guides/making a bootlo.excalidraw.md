---

excalidraw-plugin: parsed
tags: [excalidraw]

---
==⚠  Switch to EXCALIDRAW VIEW in the MORE OPTIONS menu of this document. ⚠== You can decompress Drawing data with the command palette: 'Decompress current Excalidraw file'. For more info check in plugin settings under 'Saving'



# test
# Магическое число

  

Магическое число является самой важной частью

загрузчика. Без него BIOS не имел бы представления

о том, с каких дисков он может (или не может) загружаться.

Это потенциально могло бы привести к повреждению или потере

данных, или даже к возможному отказу оборудования.

  

## 0xAA55

  

Чтобы предотвратить это, BIOS ищет `0xAA55` в

конце загрузочного сектора. "Сектор" определяется

BIOS как первые 512 байт каждого диска. Это означает,

что у нас есть только 512 байт для хранения всего кода

загрузчика! Очевидно, современный загрузчик более сложен,

чем это, но мы разберемся с этим позже.

  

## Сборка

  

Прежде чем мы начнем, убедитесь, что вы можете собрать

пример `boot.asm`. Вы должны иметь возможность сделать это

с помощью команды:

  

```sh

nasm boot.asm

```

  

Затем вы должны иметь возможность загрузить пример в

QEMU и запустить его следующей командой:

  

```sh

qemu-system-x86_64 -drive format=raw,file=boot

```

  

Поначалу он не будет делать много, но это нормально!

Пока QEMU не вылетает и экран не мерцает, загрузчик

работает как ожидается. Когда вы закончите писать свой,

он должен выглядеть так же.

  

## Первая загрузка

  

На данный момент наш загрузчик будет самой простой программой,

известной человеку: бесконечным циклом. В NASM есть несколько

специальных символов, которые мы можем использовать здесь:

`$` и `$$`.

  

В NASM `$` заменяется адресом **текущей инструкции** во время

сборки. Аналогично, `$$` заменяется адресом **предыдущей

инструкции**.

  

Прежде чем двигаться дальше, попробуйте реализовать этот простой

загрузочный сектор самостоятельно. Посмотрите, сможете ли вы

заставить его работать с магическим числом.

  

Это означает, что для создания бесконечного цикла мы можем просто

использовать простую инструкцию

  

```asm

jmp $

```

  

(или прыжок на текущую инструкцию) как нашу единственную

инструкцию. Затем нам нужно будет заполнить остальную часть

нашего загрузочного сектора и записать магическое число.

  

## Сырые данные

  

Чтобы заставить магическое число работать, нам нужно

иметь возможность записывать сырые данные непосредственно в файл.

В NASM есть несколько функций для этого:

  

- `db` (Define Byte - Определить байт)

- `dw` (Define Word - Определить слово)

- `dd` (Define Doubleword - Определить двойное слово)

- `dq` (Define Quadword - Определить четверное слово)

  

Эти функции записывают сырые данные длиной 8,

16, 32 и 64 бита соответственно. (Это также

1, 2, 4 и 8 байт). Поскольку магическое число имеет длину

16 бит, мы будем использовать `dw` для его определения:

  

```asm

dw 0xAA55

```

  

Теперь нам нужно заполнить остальную часть файла нулевыми

байтами, чтобы убедиться, что наше магическое число является

последними двумя байтами загрузочного сектора. Вы можете найти

команду [times](https://nasm.us/doc/nasmdoc3.html) особенно

полезной для этого. Если вы застряли, есть подробное объяснение

в исходном файле, так что просто посмотрите там!

  

Удачи!# Магическое число

  

Магическое число является самой важной частью

загрузчика. Без него BIOS не имел бы представления

о том, с каких дисков он может (или не может) загружаться.

Это потенциально могло бы привести к повреждению или потере

данных, или даже к возможному отказу оборудования.

  

## 0xAA55

  

Чтобы предотвратить это, BIOS ищет `0xAA55` в

конце загрузочного сектора. "Сектор" определяется

BIOS как первые 512 байт каждого диска. Это означает,

что у нас есть только 512 байт для хранения всего кода

загрузчика! Очевидно, современный загрузчик более сложен,

чем это, но мы разберемся с этим позже.

  

## Сборка

  

Прежде чем мы начнем, убедитесь, что вы можете собрать

пример `boot.asm`. Вы должны иметь возможность сделать это

с помощью команды:

  

```sh

nasm boot.asm

```

  

Затем вы должны иметь возможность загрузить пример в

QEMU и запустить его следующей командой:

  

```sh

qemu-system-x86_64 -drive format=raw,file=boot

```

  

Поначалу он не будет делать много, но это нормально!

Пока QEMU не вылетает и экран не мерцает, загрузчик

работает как ожидается. Когда вы закончите писать свой,

он должен выглядеть так же.

  

## Первая загрузка

  

На данный момент наш загрузчик будет самой простой программой,

известной человеку: бесконечным циклом. В NASM есть несколько

специальных символов, которые мы можем использовать здесь:

`$` и `$$`.

  

В NASM `$` заменяется адресом **текущей инструкции** во время

сборки. Аналогично, `$$` заменяется адресом **предыдущей

инструкции**.

  

Прежде чем двигаться дальше, попробуйте реализовать этот простой

загрузочный сектор самостоятельно. Посмотрите, сможете ли вы

заставить его работать с магическим числом.

  

Это означает, что для создания бесконечного цикла мы можем просто

использовать простую инструкцию

  

```asm

jmp $

```

  

(или прыжок на текущую инструкцию) как нашу единственную

инструкцию. Затем нам нужно будет заполнить остальную часть

нашего загрузочного сектора и записать магическое число.

  

## Сырые данные

  

Чтобы заставить магическое число работать, нам нужно

иметь возможность записывать сырые данные непосредственно в файл.

В NASM есть несколько функций для этого:

  

- `db` (Define Byte - Определить байт)

- `dw` (Define Word - Определить слово)

- `dd` (Define Doubleword - Определить двойное слово)

- `dq` (Define Quadword - Определить четверное слово)

  

Эти функции записывают сырые данные длиной 8,

16, 32 и 64 бита соответственно. (Это также

1, 2, 4 и 8 байт). Поскольку магическое число имеет длину

16 бит, мы будем использовать `dw` для его определения:

  

```asm

dw 0xAA55

```

  

Теперь нам нужно заполнить остальную часть файла нулевыми

байтами, чтобы убедиться, что наше магическое число является

последними двумя байтами загрузочного сектора. Вы можете найти

команду [times](https://nasm.us/doc/nasmdoc3.html) особенно

полезной для этого. Если вы застряли, есть подробное объяснение

в исходном файле, так что просто посмотрите там!

  

Удачи!
# Магическое число

Магическое число является самой важной частью
загрузчика. Без него BIOS не имел бы представления
о том, с каких дисков он может (или не может) загружаться.
Это потенциально могло бы привести к повреждению или потере
данных, или даже к возможному отказу оборудования.

## 0xAA55

Чтобы предотвратить это, BIOS ищет `0xAA55` в
конце загрузочного сектора. "Сектор" определяется
BIOS как первые 512 байт каждого диска. Это означает,
что у нас есть только 512 байт для хранения всего кода
загрузчика! Очевидно, современный загрузчик более сложен,
чем это, но мы разберемся с этим позже.

## Сборка

Прежде чем мы начнем, убедитесь, что вы можете собрать
пример `boot.asm`. Вы должны иметь возможность сделать это
с помощью команды:

```sh
nasm boot.asm
```

Затем вы должны иметь возможность загрузить пример в
QEMU и запустить его следующей командой:

```sh
qemu-system-x86_64 -drive format=raw,file=boot
```

Поначалу он не будет делать много, но это нормально!
Пока QEMU не вылетает и экран не мерцает, загрузчик
работает как ожидается. Когда вы закончите писать свой,
он должен выглядеть так же.

## Первая загрузка

На данный момент наш загрузчик будет самой простой программой,
известной человеку: бесконечным циклом. В NASM есть несколько
специальных символов, которые мы можем использовать здесь:
` и `$`.

В NASM ` заменяется адресом **текущей инструкции** во время
сборки. Аналогично, `$` заменяется адресом **предыдущей
инструкции**.

Прежде чем двигаться дальше, попробуйте реализовать этот простой
загрузочный сектор самостоятельно. Посмотрите, сможете ли вы
заставить его работать с магическим числом.

Это означает, что для создания бесконечного цикла мы можем просто
использовать простую инструкцию

```asm
jmp $
```

(или прыжок на текущую инструкцию) как нашу единственную
инструкцию. Затем нам нужно будет заполнить остальную часть
нашего загрузочного сектора и записать магическое число.

## Сырые данные

Чтобы заставить магическое число работать, нам нужно
иметь возможность записывать сырые данные непосредственно в файл.
В NASM есть несколько функций для этого:

- `db` (Define Byte - Определить байт)
- `dw` (Define Word - Определить слово)
- `dd` (Define Doubleword - Определить двойное слово)
- `dq` (Define Quadword - Определить четверное слово)

Эти функции записывают сырые данные длиной 8,
16, 32 и 64 бита соответственно. (Это также
1, 2, 4 и 8 байт). Поскольку магическое число имеет длину
16 бит, мы будем использовать `dw` для его определения:

```asm
dw 0xAA55
```

Теперь нам нужно заполнить остальную часть файла нулевыми
байтами, чтобы убедиться, что наше магическое число является
последними двумя байтами загрузочного сектора. Вы можете найти
команду [times](https://nasm.us/doc/nasmdoc3.html) особенно
полезной для этого. Если вы застряли, есть подробное объяснение
в исходном файле, так что просто посмотрите там!

Удачи!

# Excalidraw Data

## Text Elements
# Магическое число

Магическое число является самой важной частью
загрузчика. Без него BIOS не имел бы представления
о том, с каких дисков он может (или не может) загружаться.
Это потенциально могло бы привести к повреждению или потере
данных, или даже к возможному отказу оборудования.

## 0xAA55

Чтобы предотвратить это, BIOS ищет `0xAA55` в
конце загрузочного сектора. "Сектор" определяется
BIOS как первые 512 байт каждого диска. Это означает,
что у нас есть только 512 байт для хранения всего кода
загрузчика! Очевидно, современный загрузчик более сложен,
чем это, но мы разберемся с этим позже.

## Сборка

Прежде чем мы начнем, убедитесь, что вы можете собрать
пример `boot.asm`. Вы должны иметь возможность сделать это
с помощью команды:

```sh
nasm boot.asm
```

Затем вы должны иметь возможность загрузить пример в
QEMU и запустить его следующей командой:

```sh
qemu-system-x86_64 -drive format=raw,file=boot
```

Поначалу он не будет делать много, но это нормально!
Пока QEMU не вылетает и экран не мерцает, загрузчик
работает как ожидается. Когда вы закончите писать свой,
он должен выглядеть так же.

## Первая загрузка

На данный момент наш загрузчик будет самой простой программой,
известной человеку: бесконечным циклом. В NASM есть несколько
специальных символов, которые мы можем использовать здесь:
`$` и `$$`.

В NASM `$` заменяется адресом **текущей инструкции** во время
сборки. Аналогично, `$$` заменяется адресом **предыдущей
инструкции**.

Прежде чем двигаться дальше, попробуйте реализовать этот простой
загрузочный сектор самостоятельно. Посмотрите, сможете ли вы
заставить его работать с магическим числом.

Это означает, что для создания бесконечного цикла мы можем просто
использовать простую инструкцию

```asm
jmp $
```

(или прыжок на текущую инструкцию) как нашу единственную
инструкцию. Затем нам нужно будет заполнить остальную часть
нашего загрузочного сектора и записать магическое число.

## Сырые данные

Чтобы заставить магическое число работать, нам нужно
иметь возможность записывать сырые данные непосредственно в файл.
В NASM есть несколько функций для этого:

- `db` (Define Byte - Определить байт)
- `dw` (Define Word - Определить слово)
- `dd` (Define Doubleword - Определить двойное слово)
- `dq` (Define Quadword - Определить четверное слово)

Эти функции записывают сырые данные длиной 8,
16, 32 и 64 бита соответственно. (Это также
1, 2, 4 и 8 байт). Поскольку магическое число имеет длину
16 бит, мы будем использовать `dw` для его определения:

```asm
dw 0xAA55
```

Теперь нам нужно заполнить остальную часть файла нулевыми
байтами, чтобы убедиться, что наше магическое число является
последними двумя байтами загрузочного сектора. Вы можете найти
команду [times](https://nasm.us/doc/nasmdoc3.html) особенно
полезной для этого. Если вы застряли, есть подробное объяснение
в исходном файле, так что просто посмотрите там!

Удачи!
 ^wUS8uZMn

%%
## Drawing
```compressed-json
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=
```
%%