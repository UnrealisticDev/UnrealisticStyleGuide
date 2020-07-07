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
the foundation for this style guide.*)

### Linter

There is an Editor plugin available on the [Marketplace](https://www.unrealengine.com/marketplace/en-US/product/remapt-input-remapping-system) that allows you to easily enforce the asset styling conventions
in this guide (or to edit those conventions to fit your needs).

### Discussion

To discuss this style guide, add a comment to the dedicated page on [Unrealistic.dev](https://www.unrealistic.dev/unrealistic-style-guide).

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

### 1.3 Naming Conventions

Pair the base and variant of your asset with the following modifiers to calculate the final name for your asset.

#### 1.3.1 Object Blueprints

| Asset Type | Prefix | Suffix | Notes |
| Object Blueprint | BP_| | |  

Many things come with Blueprint scripting - Objects, Actors, Widgets, etc. This has led to the unfortunate practice of using the `BP_` prefix with *anything* that incorporates Blueprint scripting. This practice leads to a Content directory full of `BP_` prefixed assets, with no way to tell what each one is without looking at the thumbnail or opening the asset.

We can do better than that. Only apply the `BP_` prefix to Object Blueprints. Do not apply the prefix to:

* Actors
* Widget Blueprints
* Anything else

#### 1.3.2 Gameplay Core

| Asset Type | Prefix | Suffix | Notes |
| Actor | ACT_| | |
| Pawn | PWN_| | |
| PlayerController | PC_| | |
| PlayerState | PS_| | |
| GameModeBase | GM_| | |
| GameStateBase | GS_ | | |
| GameInstance | GI_| | |

(*Coming soon...*)

## Code

(*Coming soon...*)

## Project

(*Coming soon...*)
