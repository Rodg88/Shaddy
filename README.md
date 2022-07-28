# Shaddy

![license](https://img.shields.io/github/license/Icecovery/Shaddy?style=for-the-badge)
![spacedockDownloads](http://img.shields.io/badge/dynamic/json?style=for-the-badge&?color=66adff&label=downloads&query=%24.downloads&suffix=+&url=https%3A%2F%2Fspacedock.info%2Fapi%2Fmod%2F3064)
![spacedockFollowers](http://img.shields.io/badge/dynamic/json?style=for-the-badge&?color=1ec92a&label=followers&query=%24.followers&suffix=+&url=https%3A%2F%2Fspacedock.info%2Fapi%2Fmod%2F3064)
![modVersion](https://img.shields.io/badge/dynamic/json?style=for-the-badge&?color=f2b02c&label=latest%20version&query=versions%5B%3A1%5D.friendly_version&url=https%3A%2F%2Fspacedock.info%2Fapi%2Fmod%2F3064)
![kspVersion](https://img.shields.io/badge/dynamic/json?style=for-the-badge&?color=c44221&label=Build%20for&prefix=KSP%20&query=versions%5B%3A1%5D.game_version&url=https%3A%2F%2Fspacedock.info%2Fapi%2Fmod%2F3064)

Shaddy is a collection of shaders made for Kerbal Space Program, not to be confused with [Shabby](https://github.com/taniwha/Shabby), a shader asset bundle loader that you most likely also need to use to load Shaddy shaders :)

---

## Usage

### If you are a player...

Shaddy does not do anything by itself, it is designed to be used by other mods. If you run into any problem with the shader please feel free to report it as an issue.

### If you are a modder...

You may want to use [Shabby](https://github.com/taniwha/Shabby) to load Shaddy shaders to your parts. Alternatively, you can also use your own shader loader.

To start making mods using Shaddy:

* First download the SDK in [GitHub Release](https://github.com/Icecovery/Shaddy/releases).

* Then, import the downloaded unitypackage to your unity project. 

* You should now see a folder named `Shaders` appear under your Assets folder.

* Create material that uses these new shaders.

* Export the part as if it is using stock KSP shaders, and ignore the Part Tool warning on using a stock shader.

* Install Shaddy from CKAN or [SpaceDock](https://spacedock.info/mod/3064/Shaddy) to GameData.

* If you are using [Shabby](https://github.com/taniwha/Shabby) to load Shaddy shaders, make sure it is installed, too.

* Open the game and make sure the shader is loaded correctly on the part.

* ???

* Profit.

Notes:

All Shaddy/Translucent shaders are double-sided (No back face or front face culling). This means if you are making a parachute or a leaf model that has the same texture on both sides, you don't have to duplicate the mesh and then flip the faces, one-sided mesh will work just as fine as a double-sided one.

---

## Download

For players: [SpaceDock](https://spacedock.info/mod/3064/Shaddy)

For modders: [SDK](https://github.com/Icecovery/Shaddy/releases)

---

## Demo

<details>
<summary><b>Click to Expand</b></summary>

[Shaddy/Translucent](#shaddytranslucent) shader comparing with KSP/Diffuse shader on a stock parachute

![](Media/StockChuteCompare.png)

Parachute LOD effect, see [Setup Parachute LOD](#setup-parachute-lod) section on how to set it up.

![](Media/RopeLOD.gif)

[Shaddy/Translucent Cutoff (Mapped) (Bumped)](#shaddytranslucent-cutoff-mapped-bumped) shader comparing with KSP/Alpha/Cutoff (Bumped) on a leaf

Front

![](Media/Leaf-Front.png)

Back

![](Media/Leaf-Back.png)

[Shaddy/Translucent Specular](#shaddytranslucent-specular) shader comparing with KSP/Specular on the stock large solar panel

Front

![](Media/StockSolarCompare-Front.png)

Back

![](Media/StockSolarCompare-Back.png)

[Shaddy/Translucent Specular](#shaddytranslucent-specular) shader's look when interacting with light

![](Media/StockSolarLight.gif)


[Shaddy/Translucent Specular (Mapped)](#shaddytranslucent-specular-mapped) shader on a plane that vaguely represents the solar panels on the ISS

Front

![](Media/ISSSolar-Front.png)

Back

![](Media/ISSSolar-Back.png)

</details>

---

## Available Shaders

### Manifest

| Name                                                                                  | Render Queue |
|---------------------------------------------------------------------------------------|:------------:|
| [Translucent](#shaddytranslucent)                                                     | 2000         |
| [Translucent (Bumped)](#shaddytranslucent-bumped)                                     | 2000         |
| [Translucent (Mapped)](#shaddytranslucent-mapped)                                     | 2000         |
| [Translucent (Mapped) (Bumped)](#shaddytranslucent-mapped-bumped)                     | 2000         |
| [Translucent Specular](#shaddytranslucent-specular)                                   | 2000         |
| [Translucent Specular (Bumped)](#shaddytranslucent-specular-bumped)                   | 2000         |
| [Translucent Specular (Mapped)](#shaddytranslucent-specular-mapped)                   | 2000         |
| [Translucent Specular (Mapped) (Bumped)](shaddytranslucent-specular-mapped-bumped)    | 2000         |
| [Translucent Cutoff](#shaddytranslucent-cutoff)                                       | 2450         |
| [Translucent Cutoff (Bumped)](#shaddytranslucent-cutoff-bumped)                       | 2450         |
| [Translucent Cutoff (Mapped)](#shaddytranslucent-cutoff-mapped)                       | 2450         |
| [Translucent Cutoff (Mapped) (Bumped)](#shaddytranslucent-cutoff-mapped-bumped)       | 2450         |
| [Translucent (Monocolor)](#shaddytranslucent-monocolor)                               | 2000         |
| [Translucent (Monocolor) (Clip Out)](#shaddytranslucent-monocolor-clip-out)           | 2450         |
| [Translucent (Monocolor) (Fade In)](#shaddytranslucent-monocolor-fade-in)             | 3000         |

### Common Properties

| Property             | Type    | Description |
|----------------------|---------|-------------|
| `_Color`             | Color   | The base color of a one-colored object |
| `_MainTex`           | Texture | Base color / albedo / diffuse map of the object |
| `_BumpMap`           | Texture | Normal / bump map of the object |
| `_SpecColor`         | Color   | The color of the specular highlight. Works in the same way as in KSP/Specular |
| `_Shininess`         | Float   | Controls how shiny the specular highlight is. Works in the same way as in KSP/Specular |
| `_TransmissionColor` | Color   | Controls the color of the surface when the light source is behind the surface |
| `_TransmissionMap`   | Texture | Per-pixel transmission color map |
| `_TransmissionPower` | Float   | Value multiplier of the transmission map |
| `_AmbientBase`       | Float   | Controls how much the ambient light affect the surface color |

### Shaddy/Translucent

Most basic translucent shader.

| Property             | Type    | Range    | Note |
|----------------------|---------|----------|------|
| `_MainTex`           | Texture |          |      |
| `_TransmissionColor` | Color   | HDR      |      |
| `_AmbientBase`       | Float   | 0 - 1    |      |

### Shaddy/Translucent (Bumped)

Shaddy/Translucent but with normal map support

| Property             | Type    | Range    | Note |
|----------------------|---------|----------|------|
| `_MainTex`           | Texture |          |      |
| `_BumpMap`           | Texture |          |      |
| `_TransmissionColor` | Color   | HDR      |      |
| `_AmbientBase`       | Float   | 0 - 1    |      |

### Shaddy/Translucent (Mapped)

Shaddy/Translucent but uses per-pixel transmission value

| Property             | Type    | Range    | Note |
|----------------------|---------|----------|------|
| `_MainTex`           | Texture |          |      |
| `_TransmissionMap`   | Texture |          |      |
| `_TransmissionPower` | Float   |          |      |
| `_AmbientBase`       | Float   | 0 - 1    |      |

### Shaddy/Translucent (Mapped) (Bumped)

Shaddy/Translucent (Bumped) but uses per-pixel transmission value

| Property             | Type    | Range    | Note |
|----------------------|---------|----------|----- |
| `_MainTex`           | Texture |          |      |
| `_BumpMap`           | Texture |          |      |
| `_TransmissionMap`   | Texture |          |      |
| `_TransmissionPower` | Float   |          |      |
| `_AmbientBase`       | Float   | 0 - 1    |      |

### Shaddy/Translucent Specular

KSP/Specular but translucent

| Property             | Type    | Range    | Note |
|----------------------|---------|----------|------|
| `_MainTex`           | Texture |          | Alpha channel controls glossiness, same as KSP/Specular |
| `_SpecColor`         | Color   |          |      |
| `_Shininess`         | Float   | 0.03 - 1 |      |
| `_TransmissionColor` | Color   | HDR      |      |
| `_AmbientBase`       | Float   | 0 - 1    |      |

### Shaddy/Translucent Specular (Bumped)

KSP/Bumped Specular but translucent

| Property             | Type    | Range    | Note |
|----------------------|---------|----------|------|
| `_MainTex`           | Texture |          | Alpha channel controls glossiness, same as KSP/Specular |
| `_SpecColor`         | Color   |          |      |
| `_Shininess`         | Float   | 0.03 - 1 |      |
| `_BumpMap`           | Texture |          |      |
| `_TransmissionColor` | Color   | HDR      |      |
| `_AmbientBase`       | Float   | 0 - 1    |      |

### Shaddy/Translucent Specular (Mapped)

KSP/Specular but uses per-pixel transmission value

| Property             | Type    | Range    | Note |
|----------------------|---------|----------|------|
| `_MainTex`           | Texture |          | Alpha channel controls glossiness, same as KSP/Specular |
| `_SpecColor`         | Color   |          |      |
| `_Shininess`         | Float   | 0.03 - 1 |      |
| `_TransmissionMap`   | Texture |          |      |
| `_TransmissionPower` | Float   |          |      |
| `_AmbientBase`       | Float   | 0 - 1    |      |

### Shaddy/Translucent Specular (Mapped) (Bumped)

KSP/Bumped Specular but uses per-pixel transmission value

| Property             | Type    | Range    | Note |
|----------------------|---------|----------|----- |
| `_MainTex`           | Texture |          | Alpha channel controls glossiness, same as KSP/Specular |
| `_SpecColor`         | Color   |          |      |
| `_Shininess`         | Float   | 0.03 - 1 |      |
| `_BumpMap`           | Texture |          |      |
| `_TransmissionMap`   | Texture |          |      |
| `_TransmissionPower` | Float   |          |      |
| `_AmbientBase`       | Float   | 0 - 1    |      |

### Shaddy/Translucent Cutoff

Shaddy/Translucent with alpha clipping

| Property             | Type    | Range    | Note |
|----------------------|---------|----------|------|
| `_MainTex`           | Texture |          | Alpha channel is used for opacity clipping |
| `_TransmissionColor` | Color   | HDR      |      |
| `_AmbientBase`       | Float   | 0 - 1    |      |

### Shaddy/Translucent Cutoff (Bumped)

Shaddy/Translucent (Bumped) with alpha clipping

| Property             | Type    | Range    | Note |
|----------------------|---------|----------|------|
| `_MainTex`           | Texture |          | Alpha channel is used for opacity clipping |
| `_BumpMap`           | Texture |          |      |
| `_TransmissionColor` | Color   | HDR      |      |
| `_AmbientBase`       | Float   | 0 - 1    |      |

### Shaddy/Translucent Cutoff (Mapped)

Shaddy/Translucent (Mapped) with alpha clipping

| Property             | Type    | Range    | Note |
|----------------------|---------|----------|------|
| `_MainTex`           | Texture |          | Alpha channel is used for opacity clipping |
| `_TransmissionMap`   | Texture |          |      |
| `_TransmissionPower` | Float   |          |      |
| `_AmbientBase`       | Float   | 0 - 1    |      |

### Shaddy/Translucent Cutoff (Mapped) (Bumped)

Shaddy/Translucent (Mapped) (Bumped) with alpha clipping

| Property             | Type    | Range    | Note |
|----------------------|---------|----------|----- |
| `_MainTex`           | Texture |          | Alpha channel is used for opacity clipping |
| `_BumpMap`           | Texture |          |      |
| `_TransmissionMap`   | Texture |          |      |
| `_TransmissionPower` | Float   |          |      |
| `_AmbientBase`       | Float   | 0 - 1    |      |

### Shaddy/Translucent (Monocolor)

One-colored version of Shaddy/Translucent

| Property             | Type    | Range    | Note |
|----------------------|---------|----------|------|
| `_Color`             | Color   |          |      |
| `_TransmissionColor` | Color   | HDR      |      |
| `_AmbientBase`       | Float   | 0 - 1    |      |

### Shaddy/Translucent (Monocolor) (Clip Out)

Shaddy/Translucent (Monocolor) but will clip out after some distance, useful when combined with Shaddy/Translucent (Monocolor) (Fade In) to create parachute rope LOD effect

| Property             | Type    | Range    | Note |
|----------------------|---------|----------|------|
| `_Color`             | Color   |          |      |
| `_TransmissionColor` | Color   | HDR      |      |
| `_AmbientBase`       | Float   | 0 - 1    |      |
| `_ClipOutDistance`   | Float   |          | Object will clip out after this distance |

### Shaddy/Translucent (Monocolor) (Fade In)

Shaddy/Translucent (Monocolor) but will fade in after some distance, useful when combined with Shaddy/Translucent (Monocolor) (Clip Out) to create parachute rope LOD effect

| Property             | Type    | Range    | Note |
|----------------------|---------|----------|------|
| `_Color`             | Color   |          | The color of the fresnel effect |
| `_TransmissionColor` | Color   | HDR      |      |
| `_AmbientBase`       | Float   | 0 - 1    |      |
| `_FresnelPower`      | Float   |          | Controls the power of the fresnel effect |
| `_Opacity`           | Float   |          | Controls the opacity of the fresnel effect |
|`_FadeInStartDistance`| Float   |          | Object will start to fade in at this distance |
| `_FadeInEndDistance` | Float   |          | Object will be completely faded in at this distance|

---

## Setup Parachute LOD

<details>
<summary><b>Click to Expand</b></summary>

In this example, the Canopy is using [Translucent (Bumped)](#shaddytranslucent-bumped), Rope is using [Translucent (Monocolor) (Clip Out)](#shaddytranslucent-monocolor-clip-out), Rope (low poly) is using [Translucent (Monocolor) (Fade In)](#shaddytranslucent-monocolor-fade-in), and Rope Core is using [Translucent (Monocolor)](#shaddytranslucent-monocolor).

Canopy

![](Media/ChuteHierarchy-Canopy.png)

Rope

![](Media/ChuteHierarchy-Rope.png)

Rope Low Poly

![](Media/ChuteHierarchy-RopeLowPoly.png)

Rope Core

![](Media/ChuteHierarchy-RopeCore.png)

Basic hierarchy setup

![](Media/ChuteHierarchy.gif)

The Rope low poly model looks like this, `Cast Shadows` should be set to `Off` in the Mesh Renderer.

![](Media/ChuteHierarchy-RopeLowPoly-Wireframe.png)

</details>

---

## License

This mod is released under the [MIT License](https://github.com/Icecovery/Shaddy/blob/master/LICENSE).

Shaders are made using [Shader Forge](https://github.com/FreyaHolmer/ShaderForge).

---

## Redistribution

You are free to bundle this mod in your mod releases. You are also free or include the shaders in your own asset bundle, but be sure to change their namespace to avoid naming collision.