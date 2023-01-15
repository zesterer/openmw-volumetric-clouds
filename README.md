# Zesterer's Volumetric Cloud & Mist Mod for [OpenMW](https://openmw.org/en/)

A mod that adds raycasted volumetric clouds to Morrowind.

The goal of this mod, aside from looking pretty, is to enhance the perception of the world's scale. High view
distances are great, but they ruin the sense of immersion and mystery. Equally, a low, static view distance has the
opposite problem: you never get the opportunity to see the sights. With this mod, you'll experience the best of both
worlds: mystery and intrigue, with occasional moments of wonder when the mist clears and you can see for miles.

## Screenshots

[![Balmora at dawn](https://cdn.discordapp.com/attachments/1006899385239617587/1050450765094846514/image.png)](https://youtu.be/CwzaRQRjlcU)

*Note that these screenshots were taken with additional mods installed, such as [Morrowind Rebirth](https://www.nexusmods.com/morrowind/mods/37795/).*

<details>
    <summary>More screenshots</summary>
    <img src="https://cdn.discordapp.com/attachments/1006899385239617587/1050450764557979718/image.png" alt="Balmora at noon">
    <img src="https://cdn.discordapp.com/attachments/1006899385239617587/1050450765543657583/image.png" alt="A clear sky">
    <img src="https://cdn.discordapp.com/attachments/1006899385239617587/1050450765883379822/image.png" alt="Clouds at a distance">
    <img src="https://cdn.discordapp.com/attachments/530703252543635487/1050472615300563055/image.png" alt="A misty morning in Vivec">
</details>

## Features

- **Clouds**: Realistic, volumetric, raycasted clouds that move, swirl, and change in real time as you play
- **Mist**: Low-lying mist that comes and goes throughout the day, altering the effective view distance dynamically
- **Rayleigh scattering**: Light realistically attenuates as it moves through the atmosphere, improving the sense of depth and scale
- **Weather**: Both clouds and mist properly react to in-game weather conditions in a realistic way
- **Point glow**: An effect that adds diffuse glowing aura around light sources, dynamically changing according to mist cover
- **Interior mist**: An effect that emulates dust and water vapour in interiors
- **Improved skybox and sun rendering**: Adds a little flair to Morrowind sunsets
- **Many configurable settings**: Pick and choose what features you enable or exactly how your game looks

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
- The point glow effect works best with [Hemaris' 'Improved Lights' mod](https://www.nexusmods.com/morrowind/mods/51463/)

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

4. Enable [post-processing shaders](https://openmw.readthedocs.io/en/latest/reference/modding/settings/postprocessing.html#enabled) in your `settings.cfg`.

5. Start OpenMW and have fun!

## Enabling the mod

1. Open the in-game 'Options' menu and enable 'Post Processing' in the 'Video' tab.

2. Press F2 to open the in-game post-processing menu

3. Click on 'clouds'

4. Press shift + right arrow key to add it to the active effects list

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
