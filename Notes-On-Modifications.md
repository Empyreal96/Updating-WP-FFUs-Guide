# Notes on possible modifications to the mounted W10M FFU

This document is going to be a work in progress as I figure things out, but here you can find info on what can be done, and what cannot be done to a mounted FFU

## What can't be done
- Modifying the registry, this is because the manifests required to edit to add new/modified registry values are compressed, while there are ways to decompress the manifests, I have no idea how to compress them back up! And Windows won't boot if we have uncompressed manifests.. Only info I know is that they get compressed with MS's Delta API (msdelta.dll) (Todo: add links with info/decompression tools)
- 
