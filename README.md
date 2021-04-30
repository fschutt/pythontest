# pythontest

Test how to build an extension module for Python

## Build

```sh
RUSTFLAGS="-C target-feature=-crt-static" \
cargo build --target=x86_64-unknown-linux-musl --release

# Install systemwide
strip ./target/x86_64-unknown-linux-musl/release/libazul.so
sudo cp ./target/x86_64-unknown-linux-musl/release/libazul.so /usr/lib

# Create symlink with proper name
ln -s /usr/lib/libazul.so ./azul.so

# Execute the script
python3 ./test.py
```

## Note

PyO3 only supports Python 3+, not Python 2.7! Make sure to
run your script with `python3 ./test.py`, not regular `python`