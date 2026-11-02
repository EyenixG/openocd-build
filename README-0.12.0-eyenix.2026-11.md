# Eyenix OpenOCD 0.12.0-eyenix.2026-11

This is the Eyenix build of **OpenOCD**, made with the GNU MCU Eclipse
build scripts.

## Compliance

The current version is based on mainline OpenOCD
(https://github.com/openocd-org/openocd.git, `master`, 0.12.0+dev),
which now includes the RISC-V support previously developed in
https://github.com/riscv-collab/riscv-openocd.git (archived in 2026-07).

Source branch: `Eyenix-opt.2026-11`.

## Changes

Compared to the mainline master branch, the following changes were applied:

- RISC-V system bus block reads are queued in large batches
  (`RISCV_SBA_BATCH_ALLOC_SIZE`, 4096 scans), and the same batch size is
  used for system bus writes.
- MPSSE (FTDI) read/write buffers are 64 KiB (was 16 KiB).
- The GDB packet buffer is 1 MiB (was 16 KiB).
- `dump_image` reads 64 KiB chunks (was 4 KiB), keeping chunk ends
  16-byte aligned.

To prefer system bus access, as the previous Eyenix build did by default,
add to the target configuration:

    riscv mem_access sysbus progbuf

## Documentation

The original documentation is available in the `share/doc` folder.
