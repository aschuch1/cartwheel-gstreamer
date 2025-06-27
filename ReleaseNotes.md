## gstreamer-va and gstreamer-msdk (in gst-plugins-bad) upstream patches commits tested:

cartwheel-gstreamer: https://github.com/intel/cartwheel-gstreamer/releases/tag/2025q1 (tag: 2025q1)

## Supported Intel Platforms:
- PTL (Panther Lake - experimental)
- BMG (Battlemage)
- ARL (Arrow Lake)
- LNL (Lunar Lake)
- MTL (Meteor Lake)
- DG2 (Discrete Graphics 2)
- ADL-S (Alder Lake-S/P/N)
- TGL (Tiger Lake)
- CFL (Coffee Lake)

## Tested Features:

- Decode: VVC (8/10bit), AVC/H264, HEVC/H265 (8/10/12bit), AV1 (8/10bit), VP9 (8/10/12bit), VP8, JPEG/MJPEG, MPEG2
- Encode: AV1 (8/10), AVC/H264, HEVC/H265 (8/10/12bit), VP9 (8/10bit), VP8, JPEG/MJPEG, MPEG2
- VPP: procamp (brightness/contrast/saturation/hue), csc, deinterlace, denoise, scale, sharpen, mirroring, rotation, transpose

## Supported Features among Intel platforms:

For features supported on each Intel platform, please refer to links below:

- decode/encode features: https://github.com/intel/media-driver/#decodingencoding-features
- VPP features: https://github.com/intel/media-driver/#video-processing-features

## Build configures
GStreamer build configure:

```shell
meson -Dprefix=$ROOT_INSTALL_DIR -Dlibdir=$ROOT_INSTALL_DIR/lib -Dbase=enabled -Dgood=enabled -Dugly=enabled -Dbad=enabled -Dgst-plugins-bad:va=enabled -Dgst-plugins-bad:msdk=enabled build
ninja -C build
ninja -C build install
```

## Reference Configure Used: Intel Libva/iHD driver, MediaSDK, oneVPL and oneVPL GPU Runtime
- VPL Dispatcher: intel/libvpl@c45b5d7
- VPL Runtime: intel/vpl-gpu-rt@93b58fb
- Media SDK: Intel-Media-SDK/MediaSDK@7a72de3
- Media driver: intel/media-driver@cf4cd1d
- Libva: intel/libva@0d1d351
- Libva-utils: intel/libva-utils@deff975
- Gmmlib: intel/gmmlib@af5f033
- Binary: these components binary of media stack (LibVA/iHD/VPL/GmmLib) can be found from https://github.com/intel/libvpl/releases

## New Details
2025Q1:
- Clean up patches for gstreamer 1.26.1 release
- Enable gstreamer-va VVC decode support
- Gstreamer experimental support for PTL

2024Q4:
- GStreamer added Intel new BMG platforms support

2024Q3:
- GStreamer added Intel new LNL and ARL platforms support
- gstreamer-msdk and gstreamer-va supported Intel new XE driver
- gstreamer-msdk msdkvpp added interpolation mode for scaling
- gstreamer-va added vajpengenc support

2024Q2:
- gstreamer-va added VVC decode support
- gstreamer-msdk add main-422-12 profile to hevc encoder
- gstreamer-msdk BGRx format in mjpegenc
- gstreamer-msdk Fix encoding incomplete issue in multi-channel vpp -included transcoding case

2024Q1:
- cartwheel-gstreamer patches supported the latest gstreamer 1.24 release
- Prioritize va memory when dynamically creating caps
- Fix lots of memory leaks
- Fix msdkvpp dma caps negotiation issue
- Fix issue of va-plugins mix with msdk-plugins in multi-channel case

2023Q4:
- GStreamer added Intel new MTL platform support
- both gstreamer-msdk and gst-va can support user-specified card on multi-gpu platform (such as dGPU+iGPU configure)
- gstreamer-msdk decoder support dynamic frame allocation from libvpl 2.9 version
- gstreamer-msdk add icq encode mode support

