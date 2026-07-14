# LG UT640S Homebrew Channel installer

Personal helper script for installing the webOS Homebrew Channel on an LG
`60UT640S0ZB` commercial/hotel TV running `webOS4.5_M16P3_TVSignage`.

This wraps the working flow found on this device:

- build a local HTTP mirror of RootMyTV assets;
- force the RootMyTV v2 WAM `extra_conf.sh` path;
- download the latest Homebrew Channel IPK;
- launch the install page on the TV through the webOS SSAP remote API;
- stream remote TV-side install logs back to the terminal.

## Usage

```bash
./lg-ut640s-install-hbc 192.168.0.73
```

If your TV has a different IP:

```bash
./lg-ut640s-install-hbc <tv-ip>
```

Optional environment variables:

```bash
PORT=8008 LOCAL_IP=192.168.0.199 WORKDIR=/tmp/lg-ut640s-hbc-installer ./lg-ut640s-install-hbc <tv-ip>
```

## Notes

- The TV and laptop must be on the same LAN.
- Accept the pairing prompt on the TV if one appears.
- The script does not vendor RootMyTV or Homebrew Channel payloads; it downloads
  them at runtime.
- This was created because the normal routes failed on this commercial TV:
  Content Store/Developer Mode was unavailable, Ez Download did not install the
  IPK, DejaVuln MP3 produced no `autoroot.log`, and the normal RootMyTV path
  chose the old devmode hook that did not execute on this firmware.

## Warning

Use only on hardware you own and accept the risk for. Rooting/modifying webOS can
brick a TV or require service recovery if the wrong paths are used.
