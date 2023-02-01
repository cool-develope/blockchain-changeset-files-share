This repository shares the change set files dumped from cronos chain for analysis purpose.

The change sets are stored separated for different IAVL stores in chunks with size of 1 million blocks, for example `block-0.zz` contains block 0 to 999999, `block-1000000.zz` contains block 1000000 to 1999999, the last chunk ends with the latest version, the latest version number is included in the directory name.

Check [the code comment](https://github.com/crypto-org-chain/cronos/blob/361f49263fa00f3e3d149832978542347865f236/versiondb/client/changeset.go#L23) for the format of a single change set chunk, there are also the golang implementations of encoding/decoding there.

The compression types can be detected from the file extension, `.zz` files should be read with `zlib.NewReader`, `.snappy` files should be read with `snappy.NewReader`, currently there are only `.zz` files, again, check the [golang implementation](https://github.com/crypto-org-chain/cronos/blob/361f49263fa00f3e3d149832978542347865f236/versiondb/client/changeset.go#L196) for the exact logic.