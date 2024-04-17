# A Fork of Zesterer's Volumetric Cloud & Mist Mod for [OpenMW](https://openmw.org/en/)

## Adds an artistic implementation of atmospheric scattering into the post-processing shader

Be sure to check out the original shader's description for general info about its features! Below is the description of this particular fork and its differences from the original.

## Description

Ever feel that OpenMW's sky is somewhat lacking compared to the colorful beauty that is MGE XE's sunsets and sunrises? It feels.. flat, for the lack of a better word. Well, this for of the popular Zesterer's post-processing shader seeks to address this very feeling: now, the sky (and the mist, too!) reacts to the sun when it is near the horizon at dawns and sunrises, taking on more and more of the color of the sun the closer it is to the horizon, more intensely close to the sun and less so farther from it. But that is not all! It is not a straight up gradient from sky to sun - the sun's light gets transformed by the atmosphere, yellower and redder close to the sun, and a bit bluer and greener on the edge where it blends with the original sky.

All of the colors are taken directly from the game, meaning that it is completely configurable, since it uses the weather values from OpenMW's .INI file. Moreover, if you prefer a softer look without the strong transformation of the light's color, or somewhere in-between, there is a slider, where you can find your personal perfect balance between the original sun color and the attenuated one. The slider's defalut value is 0.500, right between complete attenuation and the original color. PLay around with it!

### Minor

A detail that also needs addressing is that, in Zesterer's original shader, the values of sun color, fog color and fog density were hardcoded, which sometimes clashed with the game's own visuals. In this fork, all these are taken directly from OpenMW, ensuring there is no such clash and making the whole look much more configurable.

## Screenshots

(Please bear in mind that these were taken before some minor changes and improvements and as such are a bit off from the look you would get, but they still communicate the way this fork operates)
![image](https://github.com/natalieeatscats/openmw-volumetric-clouds-with-scattering/assets/93385001/b05975c4-f1a2-4189-97c3-f30231080489)
![image](https://github.com/natalieeatscats/openmw-volumetric-clouds-with-scattering/assets/93385001/ebdb51ff-14be-47ec-890d-8a86371242d9)
![image](https://github.com/natalieeatscats/openmw-volumetric-clouds-with-scattering/assets/93385001/df9a150f-87ab-4c41-958a-0c63851f26e5)
