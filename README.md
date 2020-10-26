# [Unrealistic](www.unrealistic.dev) Style Guide

A practical set of style conventions for assets, code, and other things in Unreal Engine 4.

## Preface

In the developer universe, there is an oft-cited mantra that there is no such thing as
"good" or "bad" style. Instead, it has been said:

> "Arguments over style are pointless. There should be a style guide, and you should follow it."
>
> [*Rebecca Murphey*](https://rmurphey.com/)

I disagree. Having come from a legal background, I can say with certainty that there
is such a thing as good and bad style, just as there is good and bad writing. Indeed,
quality lawyers spend their working lives trying to become better writers (until they
become judges, at which point all writing skill and common sense goes out the window).

There are sentences, words, and formats that convey meaning well, and then there are
sentences, words, and formats that obfuscate, confuse, and mislead. The same can be
said for software development. After all, the end user is the same in each domain: human.
As humans building for other humans (including ourselves), the empathetic thing to
do is to maintain good style to the extent we can.

With that said, the following style rules are designed as a lowest common denominator.
Each project, like each essay or brief, will have its own unique classes and logical
structure that defy one-size-fits-all classification. However, each project should strive
to follow these basic guidelines. (*Thanks are due to Michael Allar for creating
the [Gamemakin UE4 Style Guide](https://github.com/Allar/ue4-style-guide), which served as
the inspiration for this style guide.*)

### Linter

There is an Editor plugin available on the [Marketplace](https://www.unrealengine.com/marketplace/en-US/product/prefixed-asset-linter) that allows you to easily enforce the asset styling conventions
in this guide (or to edit those conventions to fit your needs).

### Discussion

To discuss this style guide, add a comment to the dedicated page on [Unrealistic.dev](https://unrealistic.dev/posts/unrealistic-style-guide).

### Structure

There are three main buckets that Unreal Engine 4 content falls into:

1. *Assets* - Anything that has a `.uasset` extension.
2. *Code* - Anything that has a `.cpp`, `.h`, or `.cs` extension.
3. *Projects* - Everything else.

This guide will approach styling using this basic structure.

## Assets

An 'asset' can mean many things in many contexts. In Unreal Engine 4, and for purposes of this guide, an asset means any file that has a `.uasset` extension.  

### 1.1 A Rule for Every Asset, and Every Asset Following Its Rule

This guide provides rules for many of the standard asset types. However, there is no way it can account for game- or project-specific assets (e.g. projectiles, quests, etc.). This does not mean that *you* should not establish rules for those assets yourself.

As new asset types get added to your project, define corresponding naming conventions for those asset types and enforce them.

### 1.2 Naming Format

The name of an asset is made up of four elements:

1. Prefix
2. Base
3. Variant
4. Suffix

A prefix is typically a combination of letters that hints at the asset type. For example, `SM_` is used for `StaticMesh`. With the exception of Blueprint Enumerations and Structures, every prefix should include an underscore (`_`). Every asset should have a prefix.

The base is the locus of the asset. For example, assets related to the character Amena would have the base `Amena` (e.g. `P_Amena_Explosion`, `T_Amena_Eyes`, etc.).

A variant is used to identify a subset of a base. For example, skeletal mesh skins of the character Amena might be `SKM_Amena_Summer`, `SKM_Amena_Sand`, `SKM_Amena_BeachParty`, etc. Generic variants should be named using two digits. For example, `SM_Tree_01`, `SM_Tree_02`, `SM_Tree_03`, etc.

A suffix is used to identify a subset of an asset type. Certain assets, such as Textures, will have various sub-types (e.g. diffuse, normal, alpha) which are not reflected in the prefix and which cannot otherwise be determined without opening up the asset itself. In these limited circumstances, a suffix can help to provide further context in a consistent way. A suffix is not a substitute for a prefix. Most assets will not have a suffix.

#### 1.2.1 Spacing and Casing

Asset names should not have spaces. Asset names should not have underscores, except for prefixes and suffixes. Bases and variants should be in [PascalCase](https://techterms.com/definition/pascalcase).

### 1.3 Naming Conventions

Pair the base and variant of your asset with the following modifiers to calculate the final name for your asset.

#### 1.3.1 Blueprints

| Asset Type | Prefix | Suffix | Notes |
| ---------- | ------ | ------ | ----- |
| Blueprint (Objects) | BP_| | |
| Blueprint Interface | BPI_| | |
| Blueprint Function Library | BPFL_| | |
| Blueprint Macro Library | BPML_| | |
| Enumeration | E | | |
| Structure | F | |

Many assets come with Blueprint scripting - Objects, Actors, Widgets, etc. This has led to the unfortunate practice of using the `BP_` prefix with *anything* that incorporates Blueprint scripting. In turn, this results in a Content directory full of `BP_` prefixed assets, with no way to tell what each one is without looking at the thumbnail or opening the asset.

We can do better than that. Only apply the `BP_` prefix to Object Blueprints. Do not apply the prefix to:

* Actors or Actor subclasses
* Widget Blueprints
* Animation Blueprints
* Anything else

#### 1.3.2 Gameplay Core

| Asset Type | Prefix | Suffix | Notes |
| ---------- | ------ | ------ | ----- |
| Component (Actor) | ACOMP_| | |
| Component (Scene) | SCOMP_| | |
| Actor | ACT_| | |
| Pawn | PWN_| | |
| Character | CH_| | |
| PlayerController | PC_| | |
| PlayerState | PS_| | |
| GameModeBase | GM_| | |
| GameStateBase | GS_ | | |
| GameInstance | GI_| | |

#### 1.3.3 Animations

| Asset Type | Prefix | Suffix | Notes |
| ---------- | ------ | ------ | ----- |
| Animation Sequence | A_| | |
| Animation Composite | AC_| | |
| Animation Montage | AM_| | |
| Animation Blueprint | ABP_| | |
| Aim Offset 1D | AO1_| | |
| Aim Offset (2D) | AO2_| | |
| Blend Space 1D | BS1_| | |
| Blend Space (2D) | BS2_| | |

##### 1.3.3.1 Skeletons

| Asset Type | Prefix | Suffix | Notes |
| ---------- | ------ | ------ | ----- |
| Rig | RIG_| | |
| Skeleton | SK_ | | |
| Skeletal Mesh | SKM_| | |
| (Skeletal) Pose Asset | SKP_| | |
| (Skeletal) Physics Asset | SKPH_| | |

#### 1.3.4 Artificial Intelligence

| Asset Type | Prefix | Suffix | Notes |
| ---------- | ------ | ------ | ----- |
| AI Controller | AIC_ | | |
| Behavior Tree | BT_ | | |
| Blackboard | BB_ | | |
| Decorator | BTDecorator_ | | |
| Service | BTService_ | | |
| Task | BTTask_ | | |

#### 1.3.5 Materials

| Asset Type | Prefix | Suffix | Notes |
| ---------- | ------ | ------ | ----- |
| Material | M_| | |
| Material (Decal) | M_|_Decal | |
| Material (Post Process) | M_|_PP | |
| Material (UI) | M_|_UI| |
| Material Function | MF_| | |
| Material Instance | MI_| | |
| Material Parameter Collection | MPC_| | |

#### 1.3.6 Textures

| Asset Type | Prefix | Suffix | Notes |
| ---------- | ------ | ------ | ----- |
| Texture | T_| | |
| Texture (Diffuse/Albedo/Base) | T_|_D | |
| Texture (Normal) | T_|_N | |
| Texture (Roughness) | T_|_R | |
| Texture (Alpha/Opacity) | T_|_A | |
| Texture (Ambient Occlusion) | T_|_O | |
| Texture (Bump) | T_|_B | |
| Texture (Emissive) | T_|_E | |
| Texture (Mask) | T_|_M | |
| Texture (Specular) | T_|_S | |
| Texture Cube | TC_| | |
| Media Texture | MT_| | |
| Render Target | RT_| | |
| Cube Render Target | CRT_| | |
| Texture Light Profile | TLP_| | |

##### 1.3.6.1 Texture Packing

From the Gamemakin LLC style guide:

>It is common practice to pack multiple layers of texture data into one texture. An example of this is packing Emissive, Roughness, Ambient Occlusion together as the Red, Green, and Blue channels of a texture respectively. To determine the suffix, simply stack the given suffix letters from above together, e.g. _ERO.
>
>It is generally acceptable to include an Alpha/Opacity layer in your Diffuse/Albedo's alpha channel and as this is common practice, adding A to the _D suffix is optional.
>
>Packing 4 channels of data into a texture (RGBA) is not recommended except for an Alpha/Opacity mask in the Diffuse/Albedo's alpha channel as a texture with an alpha channel incurs more overhead than one without.

#### 1.3.7 Meshes

| Asset Type | Prefix | Suffix | Notes |
| ---------- | ------ | ------ | ----- |
| StaticMesh | SM_| | |

#### 1.3.8 Particles

| Asset Type | Prefix | Suffix | Notes |
| ---------- | ------ | ------ | ----- |
| Particle System | P_| | |
| Niagara System | NFX_| | |
| Niagara Emitter | NFXE_| | |
| Niagara Effect Type | NFXET_| | |
| Niagara Dynamic Input Script (General) | NFXS_| | |
| Niagara Dynamic Input Script (Function) | NFXS_|_FN| |
| Niagara Dynamic Input Script (Module) | NFXS_|_MOD| |
| Niagara Parameter Collection | NFXP_| | |
| Niagara Parameter Collection Instance | NFXPI_| | |

#### 1.3.9 Physics

| Asset Type | Prefix | Suffix | Notes |
| ---------- | ------ | ------ | ----- |
| Physical Material | PHYSM_| | |
| Physical Material Mask | PHYSMM_| | |

#### 1.3.10 Sounds

| Asset Type | Prefix | Suffix | Notes |
| ---------- | ------ | ------ | ----- |
| Sound Cue | S_| | |
| Sound Wave | SW_| | |
| Sound Attenuation | SATT_| | |
| Sound Mix | SMIX_| | |
| Sound Class | SCL_| | |
| Sound Concurrency | SCN_ | | Should be named after corresponding Sound Class |

#### 1.3.11 User Interface

| Asset Type | Prefix | Suffix | Notes |
| ---------- | ------ | ------ | ----- |
| Widget Blueprint | W_| | |
| Widget Blueprint (Used In World) | W_|_World| |
| Font | FONT_| | |
| Slate Brush | SBR_| | |
| Slate Widget Style | SWS_| | |

## Code

Epic recently put a [C++ style guide](https://docs.unrealengine.com/en-US/Programming/Development/CodingStandard/index.html). It covers most use cases and should be followed absent a compelling countervailing reason.
