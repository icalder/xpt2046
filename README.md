# XPT2046 touch LCD driver

[![Crates.io](https://img.shields.io/crates/d/xpt2046.svg)](https://crates.io/crates/xpt2046)
[![Crates.io](https://img.shields.io/crates/v/xpt2046.svg)](https://crates.io/crates/xpt2046)
[![Released API docs](https://docs.rs/xpt2046/badge.svg)](https://docs.rs/xpt2046)

Rust Embeddd Hal based driver for xpt2046 touch screen driver

## Documentation
[View Complete Documentation Here](https://docs.rs/xpt2046)


![demo](touch_rust.png)

### Run calibration
```rust
touch.calibrate(&mut display, &mut Delay, &mut 0).unwrap();
info!("{:?}", touch.get_calibration_data());
display.clear(Rgb565::BLACK).unwrap();
```

### Use calibration data
```rust
let mut touch = xpt2046::Xpt2046::new(
        touch_spi,
        xpt2046_irq,
        xpt2046::Orientation::LandscapeFlipped,
    )
    .set_calibration_data(xpt2046::CalibrationData {
        alpha_x: 0.13036174,
        beta_x: -0.0004550742,
        delta_x: -35.855812,
        alpha_y: 0.000489098,
        beta_y: -0.08556033,
        delta_y: 331.9459,
    });
touch.init(&mut Delay).unwrap();
```

## License

Licensed under either of:

 * Apache License, Version 2.0, ([LICENSE-APACHE](LICENSE-APACHE) or http://www.apache.org/licenses/LICENSE-2.0)
 * MIT license ([LICENSE-MIT](LICENSE-MIT) or http://opensource.org/licenses/MIT)

at your option.

### Contribution

Unless you explicitly state otherwise, any contribution intentionally submitted for inclusion in the work by you, as defined in the Apache-2.0 license, shall be dual licensed as above, without any additional terms or conditions.
