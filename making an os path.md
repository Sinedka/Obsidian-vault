Цель: создать небольшую ОС с ядром, памятью, процессами, файловой системой и драйверами.

## Этап 1. Архитектура  компьютера

Книги:

- Computer Systems: A Programmer’s Perspective (CS:APP)
- Computer Organization and Design — Patterson & Hennessy

Изучить:

Процессор

- как CPU выполняет инструкции;
- регистры;
- режимы работы процессора;
- privilege levels;
- interrupts.

Память

Понять:

CPU
Cache

RAM

 |

Storage

Темы:

- RAM;
- virtual memory;
- MMU;
- paging;
- TLB;
- memory mapping.

Практика:

- изучить устройство ELF;
- написать простой загрузчик приложений;
- анализировать память процессов Linux.

  

Этап 2. Теория операционных систем (2 месяца)

Книги:

Основные:

- Operating Systems: Three Easy Pieces
- Modern Operating Systems — Tanenbaum

Изучить:

  

Процессы

Понять:

Program

   |

Process

   |

Thread

Темы:

- создание процессов;
- переключение задач;
- состояния процесса;
- scheduler.

  

Управление памятью

Темы:

- физическая память;
- виртуальная память;
- страницы;
- heap;
- memory protection.

  

Синхронизация

Изучить:

- mutex;
- semaphore;
- spinlock;
- race conditions;
- deadlocks.

  

Этап 3. Язык Rust для системной разработки (1–2 месяца)

Книги:

- The Rust Programming Language
- Rustonomicon

Изучить:

Основы:

- ownership;
- borrowing;
- lifetimes;
- traits;
- generics.

Без стандартной библиотеки:

Понять:

no_std

alloc

core

Практика:

Написать:

- свой allocator;
- структуры данных без std;
- работу с памятью напрямую.

  

Этап 4. Создание первого ядра (2–3 месяца)

Проект:

собственная ОС на Rust

Структура:

kernel/

 |

 ├── boot

 ├── memory

 ├── interrupts

 ├── drivers

 ├── process

 └── main

Реализовать:

Минимальное ядро

- загрузку ядра;
- вывод текста;
- panic handler;
- управление памятью.

  

Использовать:

- UEFI;
- x86-64;
- QEMU.

  

Этап 5. Память ядра (1–2 месяца)

Реализовать:

Physical Memory Manager

Управление:

RAM

 |

Frames

 |

Allocator

  

Virtual Memory Manager

Добавить:

- paging;
- page tables;
- memory mapping;
- protection.

  

Этап 6. Прерывания и железо (2 месяца)

Изучить:

- CPU exceptions;
- hardware interrupts;
- timers;
- PCI.

Реализовать:

Interrupt system

Например:

Keyboard

    |

Interrupt

    |

Kernel

  

Добавить:

- таймер;
- клавиатуру;
- базовый framebuffer.

  

Этап 7. Многозадачность (2 месяца)

Создать:

Task

 |

Scheduler

 |

CPU

Реализовать:

- процессы;
- потоки;
- переключение задач;
- очередь процессов.

Добавить:

- cooperative multitasking;
- затем preemptive multitasking.

  

Этап 8. Пользовательский режим (2 месяца)

Создать разделение:

User Space

  

    |

    syscall

  

    |

  

Kernel Space

Реализовать:

- system calls;
- запуск программ;
- изоляцию процессов.

  

Пример:

/bin/init

/bin/shell

/bin/test

  

Этап 9. Файловая система (2 месяца)

Изучить:

- FAT32;
- ext2;
- inode;
- VFS.

Реализовать:

Минимум:

open()

read()

write()

close()

Потом:

- каталоги;
- права доступа;
- кеширование.

  

Этап 10. Драйверы (3+ месяца)

Добавить:

Устройства

- клавиатура;
- мышь;
- экран;
- диски;
- PCI устройства.

  

Далее:

- USB;
- сеть;
- Wi-Fi.

  

Этап 11. Развитие ОС

Добавить:

Сеть

- Ethernet;
- TCP/IP;
- sockets.

Графику

- оконный менеджер;
- GUI;
- GPU acceleration.

Безопасность

- permissions;
- sandbox;
- encryption.

  

Книги в новом порядке

1. Computer Systems: A Programmer’s Perspective
2. Computer Organization and Design
3. Operating Systems: Three Easy Pieces
4. Modern Operating Systems
5. The Rust Programming Language
6. Rustonomicon
7. Intel/AMD Architecture Manuals
8. Linux Kernel Development
9. Design and Implementation of the FreeBSD Operating System

  

Практический маршрут проектов

|   |   |
|---|---|
|Месяц|Проект|
|1–2|изучение архитектуры компьютера|
|3–4|теория ОС|
|5|Rust для bare metal|
|6|первое ядро|
|7|память|
|8|interrupts|
|9|процессы|
|10|syscall|
|11|файловая система|
|12+|драйверы и расширение|

Этот путь ближе к современному подходу: Rust + UEFI + x86-64 + QEMU, примерно так сейчас делают многие учебные ОС.