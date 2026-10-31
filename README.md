# A³ Mixer UI

The virtual desk of [A³ Mixer](https://github.com/a3-audio/a3-mixer), the DJ
mixer of [A³ Audio](https://github.com/a3-audio/a3-system): the hardware desk's
layout on a screen, for a second operator or as a stand-in for the hardware. It
sends what the hardware sends and shows what A³ Core reports over OSC. JUCE 9 /
C++17, no audio; it is a3-mixer's submodule `a3-mixer-ui` and ships as the Debian
package `a3-desk`.

![Four StemDecks around the A³ desk and A³ Motion, each deck playing its own track](https://a3-audio.github.io/img/a3-setup.jpg)

**Documentation: https://a3-audio.github.io/a3-doc/**

- [OSC reference](https://a3-audio.github.io/a3-doc/ressources/osc.html).
  Addresses, ports and hosts come from a3-core's `a3-osc.json`.

## Build and test

JUCE 9.0.3 installed to `~/local/juce`, plus GoogleTest and `xvfb-run` for
the tests:

```bash
./test.sh                  # configure, build, run the suite on a screen of its own
./test.sh -- -R LedScale   # only some tests
```

The tests read an offline copy of the OSC truth: `$A3_OSC_TRUTH`, else
a3-core beside this checkout (`../../a3-core`, as in the a3-system umbrella),
else `/usr/share/a3/a3-osc.json`.

`tests/fixtures/desk-cases.json` is a copy of the fixture a3-mixer's Python
desk generates (`software/tests/fixtures/make_desk_cases.py`); a3-mixer's
tests hold the two equal. Change it there, then copy it here.

## Package

`packaging/stage` is the recipe a3-system's `installer/package.py` builds the
`a3-desk` package from:

```bash
python3 ../../installer/package.py . --out ~/a3-debs
```

## Licence

Code GPL-3.0-or-later, this README CC-BY-SA-4.0, trivial files CC0-1.0 — see
`.reuse/dep5` and `LICENSES/` ([REUSE](https://reuse.software/)).
