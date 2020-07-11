# hyperpixel + buster lite
Raspbian buster lite settings for openframeworks + hyperpixel in a Raspberry 3B+ or inferior.

Some settings have to be adjusted in order to run openframeworks 0.11.0 applications in Raspbian Buster lite. Then, additional settings for using the Hyperpixel (4.0) touch screen. 

### Openframeworks 0.11.0 in Raspbian Buster lite (i.e. without X11)

Openframeworks web guide for Raspberry Pi instructs to use the experimental GL drivers, "GL Driver Fake KMS or GL Driver Full". Not in this scenario: keep it on Legacy. Other than that, Raspbian and openFrameworks install it's almost the same, going all the way until instaling dependencies; run that step but don't compile yet.

Before, in the openFrameworks install folder edit this file: `libs/openFrameworksCompiled/project/linuxarmv6l/config.linuxarmv6l.default.mk`: Find the line `USE_PI_LEGACY = 0` and comment it (line 61).

```
	# USE_PI_LEGACY = 0
```

Now you can compile.

```
make Release -C /home/pi/openFrameworks/libs/openFrameworksCompiled/project
```
Everything should be fine compiling openFrameworks but neither your projetcs, nor the example apps, are going to run without an extra step.

#### Aditional steps required for each project

1. Be sure that the window App width and height (in project `src/main.app`) matches your screen resolution 
2. Add the following line to project's `config.make` file:

```
	PROJECT_LDFLAGS += -latomic
```
Now you can compile and run that project (`make` and `make run`)
