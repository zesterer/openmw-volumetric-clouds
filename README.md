# Zesterer's Volumetric Cloud & Mist Mod for [OpenMW](https://openmw.org/en/)

A mod that adds raycasted volumetric clouds to Morrowind.

The goal of this mod, aside from looking pretty, is to enhance the perception of the world's scale. High view
distances are great, but they ruin the sense of immersion and mystery. Equally, a low, static view distance has the
opposite problem: you never get the opportunity to see the sights. With this mod, you'll experience the best of both
worlds: mystery and intrigue, with occasional moments of wonder when the mist clears and you can see for miles.

[![A view over Vivec, looking north-east](https://i.imgur.com/UH4TMey.png)](https://youtu.be/CwzaRQRjlcU)
[![Mist outside Vivec](https://i.imgur.com/eUuck8r.png)](https://youtu.be/CwzaRQRjlcU)
[![Volumetric clouds in the distance over Red Mountain](https://i.imgur.com/SaoByZR.png)](https://youtu.be/CwzaRQRjlcU)
[![Dawn in Vivec](https://i.imgur.com/C7Sm02j.png)](https://youtu.be/CwzaRQRjlcU)
[![A misty night in Seyda Neen](https://i.imgur.com/c2NTbez.png)](https://youtu.be/CwzaRQRjlcU)

## Recommendations

- This mod works well with my [shader set](https://github.com/zesterer/openmw-shaders).
- [Enable distant terrain](https://openmw.readthedocs.io/en/stable/reference/modding/settings/terrain.html#distant-terrain)
- Whack the [viewing distance](https://openmw.readthedocs.io/en/stable/reference/modding/settings/camera.html#viewing-distance)
  up as high as it can go. I use a view distance of 300,000.
- Ensure that [distant fog](https://openmw.readthedocs.io/en/stable/reference/modding/settings/fog.html#use-distant-fog)
  is disabled (this mod supersedes it)
- Enable the FXAA post-processing shader (make sure that it comes *after* clouds in the render order)
- Disable or reduce [MSAA](https://openmw.readthedocs.io/en/stable/reference/modding/settings/video.html#antialiasing)
  (post-processing effects do not play well with it, so you're usually better off just using FXAA)

## Installing

*Ensure that you have the [latest development build](https://openmw.org/downloads/) of OpenMW. If you find that the mod
does not work with the latest development build, please open an issue!*

1. [Download the shaders](https://github.com/zesterer/openmw-volumetric-clouds/archive/refs/heads/main.zip).

2. Extract the shaders somewhere. I'd strongly suggest extracting next to your `openmw.cfg` file.

3. Add a `data` entry to your `openmw.cfg`, as with most asset mods:

```
data = "path/to/openmw-volumetric-clouds"
```

(Ensure that the `openmw-volumetric-clouds` directory contains the `shaders` and `textures` directories)

4. Start OpenMW and have fun!

## Enabling the mod

- Press F2 to open the in-game post-processing menu

- Click on 'clouds'

- Press the right arrow key to add it to the active effects list

## Configuration

The mod comes with a variety of configuration options. You can:

- Change render quality (lower quality means higher performance)

- Alter cloud density

- Alter mist density

- Toggle an additional 'swirling' effect that makes mist more realistic and interesting to watch

- Toggle clouds on and off

- Toggle whether the vanilla skybox is visible behind the clouds and mist

## Performance

Performance may be an issue for some machines. The mod includes a variety of settings (available in the aforementioned
F2 menu) that allow reducing the quality or disabling various features in order to improve performance. At minimum
settings, even the lowest-powered machines *should* be able to run the mod.

## Implementation

- Both clouds and mist are rendered using raycasting, meaning that they are 3D elements of the environment: you can
  walk through them and they swirl, shift, and move in real time.

- Although all code is new to the mod, many aspects of the implementation are borrowed from my work on
  [Veloren](https://veloren.net/)'s cloud shaders.

## Known issues

- Rain is applied before post-processing shaders and don't write to the depth buffer, so clouds appear over rain drops
