FROM rust:latest AS builder
WORKDIR /compress
COPY . .
RUN cargo build --release

FROM debian:bookworm-slim
RUN apt-get update && apt-get install -y libgcc1

COPY --from=builder /compress/target/release/rust-compressor /compress/rust-compressor

CMD ["/compress/rust-compressor"]