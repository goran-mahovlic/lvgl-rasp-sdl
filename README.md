# LVGL application for Raspberry Pi 3

"Demo printer" LVGL application for Raspbery Pi CM4 using SDL library.
This project was made from `lvgl-port-linux-frame-buffer`

## Dependencies
- Raspberry Pi CM4 (other versions was not tested!)
- LVGL (core, drivers and examples)
- ARM Linux GCC (`aarch64`)
- SDL2 library for ARM Linux

## Cloning repository
```bash
$ git clone https://github.com/goran-mahovlic/lvgl-rasp-sdl.git
```

## Building the application
```bash
$ make -j
```
To clear the build
```bash
$ make -j clean
```
The binary is saved in `build/bin` as `lvgl_app`.

## Runing the application
```bash
$ ./build/bin/lvgl_app
```

## GUI application
- Create an example project on GUI-Guider
- Copy the following directories to your project directory:
	- custom/
	- generated/
	- import/
  
If you want to add these directories in a GUI-Guider specific directory
you need to change some `makefiles`.

Change from `$(PRJ_DIR)/` to `$(PRJ_DIR)/gui_guider/` in the following `makefiles`:
```bash
- generated.mk
- images.mk
- custom.mk
- guider_fonts.mk
- guider_customer_fonts.mk
```

- Declare a GUI-Guider struct on your code:
```c
lv_ui guider_ui;
```

- Call the following functions on your startup code (after `lv_init()`):
```c
setup_ui(&guider_ui);
events_init(&guider_ui);
custom_init(&guider_ui);
```

Many thanks to author of original repo: 

https://github.com/JON95Git

https://github.com/JON95Git/lvgl-rasp-sdl
