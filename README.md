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

```bash
./extract <relative_windows_pak_path>
```

**Example**

```bash
./extract Data/GameData.pak
```

### `build-images`

Takes `.dds` files, recombines them, then outputs `.png` images to `output-images`

**Usage**

```bash
./build-images <directory> <filename_start>
```

**Example**

```bash
./build-images output/Data/GameData/Libs/UI/Textures/Maps globalMap
```

### `combine-images`

Combines image tiles that were output by `build-images`.

**Usage**

```bash
./combine-images <file_prefix> <lower_bound> <upper_bound> <grid>
```

**Example**

```bash
./combine-images globalMap 1 16 4x4
```

### `generate-map-tiles`

Convert a large image into map tiles for using with a mapping tool.

**Usage**

```bash
./combine-images <image_file>
```

**Example**

```bash
./combine-images globalMap
```