# ScreenMouseKeyboard

Prosta biblioteka edukacyjna oparta o SDL2 pozwalająca szybko tworzyć okna, rysować podstawowe figury 2D oraz obsługiwać klawiaturę i mysz.

## Funkcje

- tworzenie okna SDL2
- obsługa zdarzeń klawiatury
- obsługa myszy
- wyświetlanie tekstu (SDL2_ttf)
- rysowanie prostokątów
- rysowanie okręgów
- rysowanie linii
- rysowanie trójkątów
- rysowanie elips
- wyświetlanie informacji diagnostycznych o myszy i klawiaturze

## Wymagania

### Linux

Pakiety:

```bash
sudo apt update

sudo apt install \
    build-essential \
    cmake \
    pkg-config \
    libsdl2-dev \
    libsdl2-ttf-dev \
    libsdl2-gfx-dev
```

### Windows (MSYS2)

Zainstaluj:

```bash
pacman -S \
    mingw-w64-ucrt-x86_64-gcc \
    mingw-w64-ucrt-x86_64-cmake \
    mingw-w64-ucrt-x86_64-pkgconf \
    mingw-w64-ucrt-x86_64-SDL2 \
    mingw-w64-ucrt-x86_64-SDL2_ttf \
    mingw-w64-ucrt-x86_64-SDL2_gfx
```

## Struktura projektu

```text
ScreenMouseKeyboard
│
├── include
│   └── Screen.hpp
│
├── src
│   ├── Screen.cpp
│   └── main.cpp
│
├── CMakeLists.txt
├── CMakePresets.json
└── README.md
```

## Budowanie projektu

### Linux Debug

```bash
cmake --preset linux-debug
cmake --build --preset linux-debug
```

### Linux Release

```bash
cmake --preset linux-release
cmake --build --preset linux-release
```

### Windows (MSYS2)

```bash
cmake --preset mingw64-debug
cmake --build --preset mingw64-debug
```

## Uruchomienie

Linux:

```bash
./build-linux-release/io
```

lub

```bash
./build-linux-debug/io
```

Windows:

```bash
.\build\io.exe
```

## Przykład

```cpp
Screen screen("SDL2 Window", 800, 600);

while (screen.isOpen())
{
    screen.pollEvents();

    screen.clear();

    screen.DrawRectangle(
        100, 100,
        200, 200,
        {255,0,0,255},
        {0,0,255,255},
        4
    );

    screen.DrawCircle(
        300, 300,
        100,
        {0,0,255,255},
        {255,255,0,255},
        4
    );

    screen.DrawKeyMouseInfo();

    screen.display();
}
```

## Dostępne metody

### Okno

```cpp
bool isOpen() const;
void pollEvents();
void clear();
void display();
```

### Figury

```cpp
void DrawRectangle(...);
void DrawCircle(...);
void DrawLine(...);
void DrawTriangle(...);
void DrawEllipse(...);
```

### Tekst

```cpp
void DrawText(...);
```

### Diagnostyka

```cpp
void DrawKeyMouseInfo();
```

## Czcionki

Projekt automatycznie używa:

### Windows

```text
C:\Windows\Fonts\arial.ttf
```

### Linux

```text
/usr/share/fonts/truetype/dejavu/DejaVuSans.ttf
```

## Licencja

MIT License