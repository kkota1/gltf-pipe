I forked this to remove react stuff but keep and modify the pipeline for general threejs webdev

## Usage

```bash
Usage
  $ npx gltfjsx [Model.glb] [options]

Options
  --output, -o        Output file name/path
  --types, -t         Add Typescript definitions
  --keepnames, -k     Keep original names
  --keepgroups, -K    Keep (empty) groups, disable pruning
  --meta, -m          Include metadata (as userData)
  --shadows, s        Let meshes cast and receive shadows
  --printwidth, w     Prettier printWidth (default: 120)
  --precision, -p     Number of fractional digits (default: 2)
  --draco, -d         Draco binary path
  --root, -r          Sets directory from which .gltf file is served
  --instance, -i      Instance re-occuring geometry
  --instanceall, -I   Instance every geometry (for cheaper re-use)
  --transform, -T     Transform the asset for the web (draco, prune, resize)
    --resolution, -R  Transform resolution for texture resizing (default: 1024)
    --simplify, -S    Transform simplification (default: false) (experimental!)
      --weld          Weld tolerance (default: 0.0001)
      --ratio         Simplifier ratio (default: 0.075)
      --error         Simplifier error threshold (default: 0.001)
  --debug, -D         Debug output
```

## Features

#### ⚡️ Auto-transform (compression, resize)

With the `--transform` flag it creates a binary-packed, draco-compressed, texture-resized (1024x1024), webp compressed, deduped, instanced and pruned *.glb ready to be consumed on a web site. It uses [glTF-Transform](https://github.com/donmccurdy/glTF-Transform). This can reduce the size of an asset by 70%-90%.

It will not alter the original but create a copy and append `[modelname]-transformed.glb`.

## Requirements

- Nodejs must be installed
- The GLTF file has to be present in your projects `/public` folder
- [three](https://github.com/mrdoob/three.js/) (>= 122.x)
