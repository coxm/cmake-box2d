# CMake-Box2D
Simple CMake file for building Box2D as a shared or static library.

## Usage
Clone this repository anywhere, and run CMake as usual, but making sure to
define `BOX2D_ROOT_DIR`. For example:

    cd "/path/to/build/dir"
    cmake -DBOX2D_ROOT_DIR="/path/to/Box2D" "/path/to/this/repo"
    make
    # Optional:
    make install


Other settings can be added as usual, e.g. `-DCMAKE_BUILD_TYPE=Debug` or
`-DBUILD_SHARED_LIBS=off`.


## Contributing
Contributions of all shapes and sizes are welcome! This project merely exists
to make my life easier building Box2D as a shared library. If it can be
extended to make *your* life easier too, that's great! I'd love to include
those changes.
