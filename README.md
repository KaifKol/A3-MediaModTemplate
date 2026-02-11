# A3-MediaModTemplate

#  English

This template allows creators to play custom music and videos in Arma 3 without embedding them directly into a mission. This keeps mission file sizes small and allows for high-quality assets to be shared across multiple scenarios.

## 1. Purpose

The primary goal of this mod is **optimization**. By moving `.ogg` (music) and `.ogv` (video) files into a mod, players only download the assets once, rather than every time the mission is updated.

* *Note: The `music` and `video` folders contain empty `.md` files used only to keep the folders visible on GitHub. **Delete them** before building the mod.*


## 2. Preparation (Renaming)

> **⚠️ Mandatory Step:** Before using this template, you must rename all instances of `MediaModTemplate` to your own unique mod name (e.g., `MyCoolMod`).

* Rename the main folder.
* Search and replace `MediaModTemplate` in `config.cpp`, `mod.cpp`, and `FileListWithMusicTracks.hpp`.
* Update the file paths in the `sound[]` and video arrays to match your new folder name.

## 3. Usage Instructions

### 🎵 Adding & Playing Music

1. **Add Files:** Place your `.ogg` files in the `music` folder.
2. **Register Tracks:** Open `FileListWithMusicTracks.hpp` and add a new class:
```cpp
class MyTrackName {
    name = "My Track Display Name";
    sound[] = {"YourModName\music\filename.ogg", db+0, 1};
    duration = 120;
};
```


3. **In-Game Command:**
```sqf
playMusic "MyTrackName";
```



### 🎬 Adding & Playing Videos

1. **Add Files:** Place your `.ogv` files in the `video` folder.
2. **In-Game Command:**
```sqf
["YourModName\video\yourvideo.ogv"] spawn BIS_fnc_playVideo;
```
*Note: Videos must be in `.ogv` (Ogg Theora) format.*

### 🔊 Adding & Playing Sound Effects (SFX)

1. **Add Files:** Place your `.ogg` files in the `sound` folder.
2. **Register Sounds:** Open `soundlist.hpp` and define your sound class using the following structure:
```cpp
class MySoundEffect {
    name = "My Sound Display Name"; // display name
    sound[] = { "YourModName\sound\filename.ogg", 1, 1, 100 }; // file, volume, pitch, maxDistance
    titles[] = {}; // subtitles
};
```


3. **In-Game Commands:**
* **Global sound:** `playSound "MySoundEffect";`
* **From an object (3D):** `player say3D "MySoundEffect";`

---

## 4. Compilation & Publishing

### Compiling to .pbo

1. Download and install **PBO Manager** or use **Arma 3 Tools (Addon Builder)**.
2. Right-click your project folder.
3. Select **PBO Manager** -> **Pack into "modname.pbo"**.
4. Ensure the resulting `.pbo` is placed inside an `@YourModName\Addons\` folder structure.

### Uploading to Steam Workshop

1. Open **Arma 3 Tools** from Steam.
2. Launch **Publisher**.
3. Select "New" and point the "Source Directory" to your `@YourModName` folder.
4. Add a title, description, and preview image.
5. Click **Publish**.

---

# Русский

Этот шаблон позволяет воспроизводить пользовательскую музыку и видео в Arma 3, не встраивая их в миссию. Это оптимизирует размер миссии и позволяет использовать тяжелые файлы в разных сценариях.

## 1. Назначение

Главная цель — **оптимизация**. Перенося файлы `.ogg` (музыка) и `.ogv` (видео) в мод, игроки скачивают их один раз, а не при каждом обновлении миссии.

* *Примечание: В папках `music` и `video` находятся пустые `.md` файлы. Они нужны только для того, чтобы пустые папки отображались в репозитории GitHub. **Удалите их** перед сборкой мода.*


## 2. Подготовка (Переименование)

> **⚠️ Важное условие:** Перед использованием необходимо переименовать все упоминания `MediaModTemplate` на ваше уникальное название (например, `MyCoolMod`).

* Переименуйте корневую папку.
* Выполните поиск и замену `MediaModTemplate` в файлах `config.cpp`, `mod.cpp`, и `FileListWithMusicTracks.hpp`.
* Обновите пути к файлам в массивах `sound[]` и путях к видео.

## 3. Инструкции по использованию

### 🎵 Добавление музыки

1. **Добавление:** Положите файлы `.ogg` в папку `music`.
2. **Регистрация:** Откройте `FileListWithMusicTracks.hpp` и добавьте новый класс:
```cpp
class MyTrackName {
    name = "Название в игре";
    sound[] = {"YourModName\music\filename.ogg", db+0, 1};
    duration = 120;
};
```


3. **Команда в игре:**
```sqf
playMusic "MyTrackName";
```



### 🎬 Добавление видео

1. **Добавление:** Положите файлы `.ogv` в папку `video`.
2. **Команда в игре:**
```sqf
["YourModName\video\yourvideo.ogv"] spawn BIS_fnc_playVideo;
```
*Примечание: Видео должно быть строго в формате `.ogv`.*

### 🔊 Добавление звуковых эффектов (SFX)

1. **Добавление:** Поместите файлы `.ogg` в папку `sound`.
2. **Регистрация:** Откройте `soundlist.hpp` и добавьте класс звука по следующему образцу:
```cpp
class MySoundEffect {
    name = "Название звука"; // Отображаемое имя
    sound[] = { "YourModName\sound\filename.ogg", 1, 1, 100 }; // Путь, громкость, высота, дистанция
    titles[] = {}; // Субтитры
};
```


3. **Команды в игре:**
* **Общий звук:** `playSound "MySoundEffect";`
* **Звук от объекта (3D):** `player say3D "MySoundEffect";`

---

## 4. Компиляция и публикация

### Сборка в .pbo

1. Используйте **PBO Manager** или **Arma 3 Tools (Addon Builder)**.
2. Нажмите правой кнопкой мыши на папку мода.
3. Выберите **PBO Manager** -> **Pack into "modname.pbo"**.
4. Поместите готовый `.pbo` в папку `@YourModName\Addons\`.

### Загрузка в Steam Workshop

1. Откройте **Arma 3 Tools** в Steam.
2. Запустите **Publisher**.
3. Нажмите "New", укажите путь к папке `@YourModName`.
4. Добавьте название, описание и картинку.
5. Нажмите **Publish**.

---

<p align="center" style="font-size: 28px; font-weight: bold;">
    Developed by the RallyPoint community
</p>
<p align="center">
  <a href="https://discord.gg/hJj45jUdjT">
    <img src="https://i.postimg.cc/pXzW7R3X/1.png" width="1500">
  </a>
</p>
