<!-- markdownlint-disable MD001 MD033 MD041 -->
<center>

# Not1MM

 ![logo](https://github.com/netw3rkd/not1mm/raw/master/not1mm/data/k6gte.not1mm.svg)

</center>

 The worlds #1 unfinished contest logger! <sup>*According to K6GTE's daughter Corinna.<sup>

[![License: GPL-3.0](https://img.shields.io/github/license/netw3rkd/not1mm?color=green)](https://github.com/netw3rkd/not1mm/blob/master/LICENSE)
[![Python: 3.10+](https://img.shields.io/badge/python-3.10%2B-green?logo=python&logoColor=white)](https://www.python.org/downloads/)
[![PyQt6](https://img.shields.io/badge/PyQt6-6.0%2B-green?logo=qt)](https://pypi.org/project/PyQt6/)
[![GitHub Issues](https://img.shields.io/github/issues/netw3rkd/not1mm?color=orange&logo=github)](https://github.com/netw3rkd/not1mm/issues)
[![GitHub Stars](https://img.shields.io/github/stars/netw3rkd/not1mm?color=yellow&logo=github)](https://github.com/netw3rkd/not1mm)
[![Platforms](https://img.shields.io/badge/platform-Linux%20%7C%20Windows%20%7C%20macOS-green)](https://github.com/netw3rkd/not1mm)
[![Code style: black](https://img.shields.io/badge/code%20style-black-000000.svg)](https://github.com/psf/black)


![main screen](https://github.com/netw3rkd/not1mm/raw/master/pic/main.png)

### The Elephant in the Room

Not1MM's interface is a blatant ripoff of N1MM. It is NOT N1MM and any problem
you have with this software should in no way reflect on their software.
  This software is originally created by K6GTE, this fork is my lame attempt at contributing back. (I've also edited a ton of stuff, check the [CHANGELOG.md](CHANGELOG.md) for details.)
  Why do this?  Because I can, boredom, and I want to attempt porting this project to windows.
    - netw3rkd - Bryan, 73 de K1BQY

### Everything past this point is from K6GTE' original repo, with some minor rearrangement. ###

### The What

Not1MM is, in my opinion, a usable amateur radio, or HAM, contest logger. It's
written in Python 3.10+, and uses Qt6 framework for the graphical interface
and SQLite for the database.

### Target Environment

The primary target for this application is Linux. It may be able to run on other
platforms, BSD and Windows. But I don't have a way, or desire, to directly support them.
I've recently purchased an M4 Mac Mini, So I'll probably put more effort into that platform as well.

### The Why

**Currently this exists for my own personal amusement**. I've recently retired
after 35+ years working for 'The Phone Company', GTE -> Verizon -> Frontier.
And being a Gentleman of Leisure, needed something to do in my free time.
I'm a casual contester and could not find any contesting software for Linux that
I wanted to use. There is [Tucnak](http://tucnak.nagano.cz/) which is very robust
and mature. It just wasn't for me.

## Code Maturity & Current Multi Multi Development Focus

Not1MM is, at times, fairly stable. Recently, it would seem that I'm desperately trying to change that. The current focus of development is adding support for [Multi Multi](Multi-Multi.md) contest operations. It is something that I have no practical experience in. So you can expect the same quality of code fit and finish.

## Features

A quick feature list, See the user manual for more details.

- Lookup, QRZ and HamQTH
- CAT Control, rigctld and flrig
- CW Keyer Interface, winkeyer and cwdaemon
- Cluster and Bandmap
- Rotator control, rotctld
- [Multi Multi](Multi-Multi.md) (The super sketchy not ready for prime time)
- N1MM Packet output for nodered
- WSJT-X FT8/FT4/ETC and FLDIGI RTTY
- ADIF and Cabrillo output.
- And *Other Stuff*

## Installation

To install not1mm please see the [installation](INSTALL.md) section.

## Documentation

Get the [user manual](https://github.com/netw3rkd/not1mm/raw/master/not1mm.pdf) as a PDF file.

## Recent Changes

See [CHANGELOG.md](CHANGELOG.md) for prior changes.

## Our Code Contributors ✨

Thank you to K6GTE for creating this project and sharing it with the rest of us!

Below is an automatically generated, list of those who've submitted PR's.

<a href="https://github.com/netw3rkd/not1mm/graphs/contributors">
  <img src="https://contrib.rocks/image?repo=netw3rkd/not1mm" alt="Avatar icons for code contributors." />
</a>
