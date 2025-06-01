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