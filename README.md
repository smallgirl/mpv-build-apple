Fork from https://github.com/mpvkit/MPVKit

## How to build
```sh
# Components:
# ass, dav1d, dovi, ffmpeg, freetype, fribidi
# harfbuzz, littlecms2, mbedtls, mpv, placebo
# shaderc, spirvcross, uchardet, unibreak, vulkan
./gradlew assemble $component_name
```

## Components
```mermaid
flowchart LR
    direction LR

    A(mpv):::decoders -.-> B{{uchardet}}:::decoders
    A                 -.-> C{{libass}}:::decoders
    A                 -->  D(ffmpeg):::decoders

    %% libass
    C -->  G{{freetype}}:::decoders
    C -->  H{{fribidi}}:::decoders
    C -->  I{{harfbuzz}}:::decoders
    C -->  B
    C -->  J{{unibreak}}:::decoders
    G -.-> I

    %% ffmpeg
    D --> E(placebo):::decoders
    D --> K{{mbedtls}}:::decoders
    D --> L{{dav1d}}:::decoders
    D --> M{{shaderc}}:::decoders
    D --> N{{vulkan}}:::decoders
    D --> C

    %% placebo
    E --> O{{dovi}}:::decoders
    E --> N
    E --> M
    E --> P{{lcms2}}:::decoders
```
