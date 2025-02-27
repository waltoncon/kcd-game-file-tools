# Kingdom Come: Deliverance game file tools

## Setup

This collection of tools has been built with WSL in mind. It accesses the Steam game directory for KCD to extract data. It also uses a `.exe` for building images ([`build-images`](#build-images)).

## References and resources used

- https://aluigi.altervista.org/quickbms.htm
- https://wiki.nexusmods.com/index.php/Modding_guide_for_KCD
- https://github.com/Madfish71/SCTextureConverter/tree/master/sctexconv
- https://github.com/kingdomcomemap/kingdomcomemap.github.io/tree/master
- https://gdal.org/en/latest/programs/gdal2tiles.html
- https://wiki.nexusmods.com/index.php/Textures_and_Images
- https://gdal.org/en/latest/programs/gdal2tiles.html

## Commands

The examples below take you through extracting, building, combining, then tiling the in-game world map.

### `extract`

Extracts game files from KCD .pak files

**Usage**

```
./extract <relative_windows_pak_path>
```

**Example**

```bash
./extract Data/GameData.pak
```

### `list`

List files within the game data

**Usage**

```
./list <type>
```

**Example**

```bash
./list maps
```

### `build-images`

Takes `.dds` files, recombines them, then outputs `.png` images to `output-images`

**Usage**

```
./build-images <directory> <file> [file ...]
```

**Example**

```bash
./build-images output/Data/GameData/Libs/UI/Textures/Maps globalMap
./build-images output/Data/GameData/Libs/UI/Textures/Maps globalMap_{1..16}
```

### `combine-images`

Combines image tiles that were output by `build-images`.

**Usage**

```
./combine-images <grid> <file> [file ...]
```

**Example**

```bash
./combine-images 4x4 globalMap_{1..16}
```

### `generate-map-tiles`

Convert a large image into map tiles for using with a mapping tool.

**Usage**

```
./combine-images <image_name>
```

**Example**

```bash
./combine-images globalMap
```