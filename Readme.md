# Unzzz
[![Unzzz v0.1.1](https://img.shields.io/badge/unzzz-v0.1.1-44dfd1.svg)](https://www.npmjs.com/package/unzzz)
![Stability: Beta](https://img.shields.io/badge/stability-beta-69b0ba.svg)

## Overview
A lightweight implementation of reading .zip files, because JSZip is a behemoth
and I'm not about that life.

For the sake of being lightweight, it only supports DEFLATE compression, and
does not crc32 check the decompressed data for validity. Aside from that, it
tries to be *very* safe and validate pretty much everything else possible.

### Usage
```JavaScript
const unzzz = require( 'unzzz' )

unzzz( pathToArchive )
  .then( archive => {
    // Iterate over all the files in the archive
    for ( let each in archive.files ) {
      // Retrieve an uncompressed buffer of the file
      archive.unzipBuffer( each )
        .then( buffer => console.log( buffer ) )
    }

    // Pull out specific files and save the uncompressed files to storage
    archive.unzipFile( 'dir/filename.ext', destination )
  })
```

## Installation
```Shell
npm install unzzz
```
or just download a .zip and throw it into a node_modules folder somewhere. You should be good to go.
