# Pi Pico W Hello World with Rust

Project will toggle an LED on GPIO15 on and off at 500ms intervals and print the number of ticks to the USB Serial Logger.

Built on [Embassy](https://github.com/embassy-rs/embassy)

### Tooling
```
cargo install elf2uf2-rs
rustup target add thumbv6m-none-eabi
```

### Run on Device

- Hold BOOTSEL while connecting device over USB
- Mount Device as USB Storage
- `cargo run --release`

### Connect to USB Serial

```
screen /dev/ttyACM0 115200
```

#### USB Serial Troubleshooting

if screen exits early it may be a permission issue
```
crw-rw----. root dialout 0 B ... /dev/ttyACM0
sudo chmod 666 /dev/ttyACM0
```

If you user is not in the `dialout` group. 
```
sudo usermod -a -G dialout $(whoami)
```

`/dev/ttyACM0` may not always be the correct path.
`cargo run` will print what it's pushing to 
```
Found pico serial on /dev/ttyACM1
```
