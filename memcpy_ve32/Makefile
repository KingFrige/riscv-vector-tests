all: test.elf

CFLAGS = -march=rv64gv -DPREALLOCATE=1 -static -mcmodel=medany -std=gnu99 -O2 \
	-ffast-math -fno-common -fno-builtin-printf -nostdlib -nostartfiles -lm -lgcc -T test.ld

test.elf: crt.S syscalls.c main.c test.S
	PATH=${RISCV}/bin LD_LIBRARY_PATH=${RISCV}/lib riscv64-unknown-elf-gcc $(CFLAGS) $^ -o $@
	PATH=${RISCV}/bin LD_LIBRARY_PATH=${RISCV}/lib riscv64-unknown-elf-objdump -D $@ > $@.dmp

clean:
	$(RM) -rf test.elf.dmp test.elf
