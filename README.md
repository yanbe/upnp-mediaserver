# DLNA/UPnP MediaServer of EPGStation for Smart TVs

This program serves recorded TV programs for Smart TVs in Home LAN, recorded by EPGStation.

More specifically, this program implements following features:

- [MediaServer:1](http://upnp.org/specs/av/UPnP-av-MediaServer-v1-Device.pdf) described in [UPnP AV Architecture:1](http://upnp.org/specs/av/UPnP-av-AVArchitecture-v1-20020625.pdf)
  - [ContentDirectory:1](http://upnp.org/specs/av/UPnP-av-ContentDirectory-v1-Service.pdf)
  - [ConnectionManager:1](http://upnp.org/specs/av/UPnP-av-ConnectionManager-v1-Service.pdf)
- Advertise services via SSDP protocol

... to communicate with smart TVs UPnP/DLNA clients.

## Compatibility

- The author confirmed DLNA/UPnP client compatibility with SmartShare app that pre-installed LG Smart TV (55UF9500, webOS 2.0, 2015 model)
- Should works (perhaps needs some modifictaion. see Hacking)

## Features

- Browsing recorded tv programs by genres, rules, channels as well as latest recorded list
- Play MPEG2-TS(raw) or encoded MP4 and Matroska (with ASS subtitle) container videos
- Byte-level seek of playing video

## Build and run

```sh
docker-compose build
docker-compose up -d
docker-compose logs
```

## Hacking

- To improve compatibility for your device or support newer formats like HEVC, VP9 or AV1 see `func fmtProtocolInfo()` in `service/contentdirectory/types.go`
  - Of cource your UPnP/DLNA client must have supports such advanced formats
- To improve content navigation see `func Setup()` in `service/contentdirectory/types.go`
- Thanks to OpenAPI support of EPGStation, API client in `epgstaiton/*` is generated by using https://github.com/deepmap/oapi-codegen

## Reference

- [OCF - MediaServer:1 and MediaRenderer:1](https://openconnectivity.org/developer/specifications/upnp-resources/upnp/mediaserver1-and-mediarenderer1/)
- [https://github.com/l3tnun/EPGStation/blob/master/doc/webapi.md]

## Caution

- Use this program in your home LAN only
- Do not service this program to open internet, or you will be sued for copyright violation

## License 

- MIT License