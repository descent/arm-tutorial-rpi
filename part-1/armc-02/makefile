kernel.img: armc-02.bin
	mv $< $@
v.o: v.s
	arm-linux-gnueabihf-gcc -O2 -mfpu=neon-vfpv4 -mfloat-abi=hard -march=armv7-a -mtune=cortex-a7 -nostartfiles -g -c $<

armc-02.o: armc-02.c
	arm-linux-gnueabihf-gcc -O2 -mfpu=neon-vfpv4 -mfloat-abi=hard -march=armv7-a -mtune=cortex-a7 -nostartfiles -g -c armc-02.c 
armc-02.elf: v.o armc-02.o 
	arm-linux-gnueabihf-ld -Ttext 0x8000 $^ -o $@
armc-02.bin: armc-02.elf
	arm-linux-gnueabihf-objcopy $< -O binary $@

clean:
	rm -rf *.o
