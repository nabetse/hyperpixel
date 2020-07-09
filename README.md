# hyperpixel
Raspberry 3B settings for openframeworks+buster+hyperpixel

This is not a basic install procedure but some settings that have to be adjusted in order to run openframeworks 0.11.0 applications in Raspbian Buster lite and, then, other settings for using the Hyperpixel (4.0) touch screen with them. 

## Openframeworks 0.11.0 in Raspbian Buster lite (without X11)

Openframeworks web instructs to use the experimental GL drivers "GL Driver Fake KMS or GL Driver Full". DON'T. T Keep it on Legacy. Other than that, Raspberry and openFrameworks install it's almost the same, install dependencies but don't compile yet.

In the openFrameworks install edit this file: `libs/openFrameworksCompiled/project/linuxarmv6l/config.linuxarmv6l.default.mk`. Find the line `USE_PI_LEGACY = 0` and comment it (line 61).

```
	# USE_PI_LEGACY = 0
```

Now you can compile

```
make Release -C /home/pi/openFrameworks/libs/openFrameworksCompiled/project
```

### Aditional steps required for each application

1. Be sure that the window App width and height (in project `src/main.app`) matches your screen resolution 
2. Add the following line to project's `config.make` file:

```
	PROJECT_LDFLAGS += -latomic
```
Now you can compile that project (`make` and `make run`)
