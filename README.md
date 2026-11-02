*This project has been created as part of the 42 curriculum by scamlett.*

# Python Module 07: Creature Factory

![Python](https://img.shields.io/badge/Python-3.10+-3776AB?logo=python&logoColor=white)
![42](https://img.shields.io/badge/42-Málaga-000000)

## Description

A module about design patterns, built as a tiny creature battle game. Fire
and water creatures come out of factories, some creatures gain extra
abilities (healing, transforming), and in the end each fighter brings a
battle strategy to a tournament.

| Part | Folder | Pattern |
|------|--------|---------|
| ex0 | `ex0/` | **Abstract Factory**: `FlameFactory` and `AquaFactory` both build a base and an evolved `Creature` (Flameling / Pyrodon, Aquabub / Torragon) |
| ex1 | `ex1/` | **Capabilities as mixins**: `HealCapability` and `TransformCapability` are combined with `Creature` through multiple inheritance |
| ex2 | `ex2/` | **Strategy**: `NormalStrategy`, `AggressiveStrategy` and `DefensiveStrategy` decide how a creature acts, and check whether it is able to |

```
battle.py      ex0 only: factories and a simple fight
capacitor.py   ex1: healing and transforming creatures
tournament.py  ex0 + ex1 + ex2: every creature with a strategy, in rounds
```

## Instructions

Run from the repository root so the `ex0`, `ex1` and `ex2` packages can be
imported:

```bash
python3 battle.py
python3 capacitor.py
python3 tournament.py
```

## What I learned

- An abstract factory hides *which* class gets created behind a common
  interface, so the battle code only talks to `CreatureFactory`
- Multiple inheritance can add a capability to a class without changing its
  parent, and `isinstance(creature, HealCapability)` tells you if it has it
- The strategy pattern moves "how to behave" out of the creature and into a
  separate object you can swap at runtime
- `is_valid()` checks protect a strategy from being used with a creature
  that cannot perform it (a defensive strategy needs a healer)
- Using `__init__.py` to give each package a clean list of exports, and
  importing between sibling packages (`ex1` reuses `ex0`)
