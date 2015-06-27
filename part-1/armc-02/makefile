all: ok_led.bin

kernel.img: ok_led.bin
	cp $< $@

v.o: v.s
	arm-linux-gnueabihf-gcc -O2 -mfpu=neon-vfpv4 -mfloat-abi=hard -march=armv7-a -mtune=cortex-a7 -nostartfiles -g -c $<

ok_led.o: ok_led.c
	arm-linux-gnueabihf-gcc -O2 -mfpu=neon-vfpv4 -mfloat-abi=hard -march=armv7-a -mtune=cortex-a7 -nostartfiles -g -c $<
ok_led.elf: v.o ok_led.o 
	arm-linux-gnueabihf-ld -Ttext 0x8000 $^ -o $@
ok_led.bin: ok_led.elf
	arm-linux-gnueabihf-objcopy $< -O binary $@

armc-02.o: armc-02.c
	arm-linux-gnueabihf-gcc -O2 -mfpu=neon-vfpv4 -mfloat-abi=hard -march=armv7-a -mtune=cortex-a7 -nostartfiles -g -c $<
armc-02.elf: v.o armc-02.o 
	arm-linux-gnueabihf-ld -Ttext 0x8000 $^ -o $@
armc-02.bin: armc-02.elf
	arm-linux-gnueabihf-objcopy $< -O binary $@

clean:
	rm -rf *.o
