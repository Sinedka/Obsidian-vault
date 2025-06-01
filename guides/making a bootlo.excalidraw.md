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
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
```
%%