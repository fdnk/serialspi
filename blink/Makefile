PKG=led
BIN=${PKG}
OBJS=${PKG}.o
MCU=atmega168

CC=avr-gcc
OBJCOPY=avr-objcopy
CFLAGS=-Os -DF_CPU=16000000L -mmcu=${MCU} -Wall
PORT=COM7

${BIN}.hex: ${BIN}.elf
	${OBJCOPY} -O ihex $< $@

${BIN}.elf: ${OBJS}
	${CC} -mmcu=${MCU} -o $@ $^

install: ${BIN}.hex
	avrdude -v -c arduino -p ${MCU} -P ${PORT} -b 19200 -U flash:w:$<

clean:
	rm -f ${BIN}.elf ${BIN}.hex ${OBJS}
