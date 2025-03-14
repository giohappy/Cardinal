# RACK PRO VS CARDINAL DIFFERENCES

This document describes the differences between Rack Pro plugin and Cardinal.  
It is not possible to know all the internal details of the official plugin due to it not being open-source,
so more technical details are best-guesses based on its behaviour.

The obvious big difference is that the official plugin is a commercial, closed-source product while Cardinal is free and open-source.

Also, the official plugin works pretty much like the free standalone where you login and download modules.  
This is intentionally not allowed/enabled in Cardinal, as the target is to make a self-contained plugin binary.
Online access is also not allowed.

Bellow follows a list of features comparing the official plugin to Cardinal.

| Feature                        | Rack Pro                  | Cardinal                        | Additional notes |
|--------------------------------|---------------------------|---------------------------------|------------------|
| Open-Source                    | No                        | Yes                             | |
| Free (of cost)                 | No                        | Yes                             | |
| Officially supported           | Yes, if you pay           | No, but you can fix it yourself | |
| Contains internal modules      | Core only                 | Everything is internal          | |
| Loads external modules         | Yes                       | No                              | |
| Supports closed-source modules | Yes                       | No                              | |
| Supports physical devices      | Yes                       | No (*)                          | CardinalNative binary provides native audio+midi as standalone |
| Plugin in AU format            | Yes                       | Yes                             | |
| Plugin in LV2 format           | No                        | Yes                             | |
| Plugin in VST2 format          | Yes                       | Yes                             | |
| Plugin in VST3 format          | Yes                       | Yes                             | |
| Plugin in CLAP format          | Yes                       | Yes                             | |
| Plugin inside itself           | No, will crash            | Yes                             | Technical limitations prevent Rack Pro from loading inside itself |
| Module processing order        | Same as insertion order   | Based on cable connections      | In Cardinal module processing order changes automatically depending on cable connections |
| Multi-threaded engine          | Yes                       | No, uses host audio thread      | Intentional in Cardinal, for removing jitter |
| Supports ARM systems           | WIP                       | Yes                             | This means Apple M1 too, yes |
| Supports BSD systems           | No                        | Yes                             | Available as FreeBSD port |
| Supports RISC-V systems        | No                        | Yes                             | |
| Synth plugin variant           | 16 ins, 16 outs           | 2 ins, 2 outs                   | |
| FX plugin variant              | 16 ins, 16 outs           | 2 ins, 2 outs                   | |
| Raw-CV plugin variant          | Unsupported               | 8 audio IO + 10 CV IO           | Available in JACK, LV2 and VST3 formats, not possible in AU and VST2 |
| Arbitrary parameter automation | Yes                       | No (*)                          | Static 24 automatable params, use Host Params/Map modules to map them to module parameters |
| Integrated plugin host         | No, Host payed separately | Yes, using Carla or Ildaeil     | |
| Host sync/timing               | Using MIDI signals        | Using dedicated module          | |
| Linux/X11 event handling       | Runs on 2nd thread        | Runs on main/GUI thread         | |
| v1 module compatibility        | No                        | No, but with less restrictions  | Module widgets can load resources at any point |
| Online phone-home              | Yes                       | No                              | Online access is strictly forbidden in Cardinal |
| Proper dark theme              | WIP                       | Yes                             | All dark panel variants have explicit permission when required |
| Proper Linux headless mode     | No, always requires X11   | Yes                             | |

Additionally, Cardinal contains the following built-in modules not present in the official plugin or standalone:

 * Admiral (never updated to v2)
 * Aria Salvatrice modules (except Arcane related modules, due to their online requirement)
 * Arable Instruments and Parable Instruments (never updated to v2)
 * Mog (never updated to v2)
 * Rackwindows (never updated to v2)
 * The DISTRHO collection, including:
   * AIDA-X
   * Audio File
   * Audio to CV Pitch converter
   * Carla Plugin Host
   * Ildaeil Host
   * glBars (OpenGL bars visualization, as seen in XMMS and XBMC/Kodi)
   * Text Editor (resizable and with syntax highlight)
   * Host Parameters (24 host-exposed parameters as CV sources)
   * Host Time (play, reset, bar, beat, tick, bar-phase and beat-phase CV sources)
   * Host CV (for the Raw-CV plugin variant, allows direct CV access to/from the DAW)
