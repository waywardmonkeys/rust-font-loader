# Font-Loader
A font loading utility written in and for rust.

Currently supported platforms:

* Windows
* Every platform supporting Fontconfig
 * Unix
 * Linux
 * (Mac, not confirmed working)
 * (Windows, but not used)

# Usage
## Linux, Unix:
Fontconfig is required on Linux and Unix, as it is the default Fontmanagement utility on these platforms.
```
sudo apt-get install libfontconfig libfontconfig1-dev
```

# Example
## Cargo.toml
```toml
[dependencies]
font-loader = "https://github.com/MSleepyPanda/rust-font-loader/"
```

## main.rs:
```rust
extern crate font_loader as fonts;

use fonts::system_fonts;

fn main() {
	// Enumerate all fonts
    let sysfonts = system_fonts::query_all();
    for string in &sysfonts {
        println!("{}", string);
    }
    
    // Get "Arial" font and output the first 50 bytes of it
	let mut property = system_fonts::FontPropertyBuilder::new().family("Arial").build();
	let (font, _) = system_fonts::get(&mut property).unwrap();
	println!("{:?}", &font[..50]);
}
```

# License

The MIT License (MIT)
Copyright (c) font-loader Developers

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
