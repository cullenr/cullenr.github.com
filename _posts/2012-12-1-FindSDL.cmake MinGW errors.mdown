---
title: SDL CMake MSYS Linker Errors
layout: post
---

I just submitted a [bug](http://public.kitware.com/Bug/view.php?id=13769) to the Kitware bug tracker as I have found a tricky little bug in the FindSDL.cmake file in the current cmake build for windows (2.8.10.1). If you are getting errors like this with the current MinGW g++ (4.6.2):

	c:/mingw/bin/../lib/gcc/mingw32/4.6.2/../../../../mingw32/lib\libSDLmain.a(SDL_win32_main.o): In function `redirect_output':
	/Users/slouken/release/SDL/SDL-1.2.15/./src/main/win32/SDL_win32_main.c:219: undefined reference to `SDL_strlcpy'
	/Users/slouken/release/SDL/SDL-1.2.15/./src/main/win32/SDL_win32_main.c:220: undefined reference to `SDL_strlcat'
	/Users/slouken/release/SDL/SDL-1.2.15/./src/main/win32/SDL_win32_main.c:243: undefined reference to `SDL_strlcpy'
	/Users/slouken/release/SDL/SDL-1.2.15/./src/main/win32/SDL_win32_main.c:244: undefined reference to `SDL_strlcat'
	c:/mingw/bin/../lib/gcc/mingw32/4.6.2/../../../../mingw32/lib\libSDLmain.a(SDL_win32_main.o): In function `console_main':
	/Users/slouken/release/SDL/SDL-1.2.15/./src/main/win32/SDL_win32_main.c:296: undefined reference to `SDL_strlcpy'
	/Users/slouken/release/SDL/SDL-1.2.15/./src/main/win32/SDL_win32_main.c:301: undefined reference to `SDL_GetError'
	/Users/slouken/release/SDL/SDL-1.2.15/./src/main/win32/SDL_win32_main.c:312: undefined reference to `SDL_SetModuleHandle'
	c:/mingw/bin/../lib/gcc/mingw32/4.6.2/../../../../mingw32/lib\libSDLmain.a(SDL_win32_main.o): In function `WinMain@16':
	/Users/slouken/release/SDL/SDL-1.2.15/./src/main/win32/SDL_win32_main.c:354: undefined reference to `SDL_getenv'
	/Users/slouken/release/SDL/SDL-1.2.15/./src/main/win32/SDL_win32_main.c:386: undefined reference to `SDL_strlcpy'
	collect2: ld returned 1 exit status

Its likely because the `SDLmain` library is added to g++ before the `SDL` library. I have hacked a line in the FindSDL.cmake file to get my projects to compile, the significant line is

    list(APPEND SDL_LIBRARY_TEMP "${SDLMAIN_LIBRARY}")

which should be changed to :

    list(INSERT SDL_LIBRARY_TEMP 0 "${SDLMAIN_LIBRARY}")
