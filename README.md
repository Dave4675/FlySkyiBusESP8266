# FlySky iBus Decoder Library

This library decoding transmitted data from FlySky i6 (not tested) or FlySky
i6x (tested).
The used reciever when testing library is FlySky FS-A8S.

Default library supported 10 channels.

## Usage
```console
git clone https://github.com/utkudarilmaz/FlySkyiBus
mv FlySkyiBus <arduino-ide-path>/libraries/
```

Then import the library to source code.
```c
#include "FlySkyiBus.h"

FlySkyiBus iBus(<rx>, <tx>);

void setup() {
	Serial.begin(115200);
	iBus.begin(115200);
}

void loop() {
	Frame *framePtr = iBus.read_serial();

	// You can get channel data using:
	Serial.println(FlySkyiBus::get_channel(framePtr, <channel>);

	// Or you can get data from using pointer.
	Serial.println(framePtr->data[<channel>]);

	delete framePtr;
}
```

## Hacking Library

Normally iBus supported 14 channels communication.

If you need more channels, edit the CHANNEL_SIZE macro on the FlySkyiBus.h
header file.
