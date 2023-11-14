
SDL 3.0 has new support for high DPI displays

Displays now have a content display scale, which is the expected scale for content based on the DPI settings of the display. For example, a 4K display might have a 2.0 (200%) display scale, which means that the user expects UI elements to be twice as big on this display, to aid in readability. You can query the display content scale using `SDL_GetDisplayContentScale()`, and when this changes you get an `SDL_EVENT_WINDOW_DISPLAY_SCALE_CHANGED` event.

The window size is now distinct from the window pixel size, and the ratio between the two is the window pixel density. If the window is created with the `SDL_WINDOW_HIGH_PIXEL_DENSITY` flag, SDL will try to match the native pixel density for the display, otherwise it will try to have the pixel size match the window size. You can query the window pixel density using `SDL_GetWindowPixelDensity()`. You can query the window pixel size using `SDL_GetWindowSizeInPixels()`, and when this changes you get an `SDL_EVENT_WINDOW_PIXEL_SIZE_CHANGED` event. You are guaranteed to get a `SDL_EVENT_WINDOW_PIXEL_SIZE_CHANGED` event when a window is created and resized, and you can use this event to create and resize your graphics context for the window.

The window has a display scale, which is the scale from the pixel resolution to the desired content size, e.g. the combination of the pixel density and the content scale. For example, a 3840x2160 window displayed at 200% on Windows, and a 1920x1080 window with the high density flag on a 2x display on macOS will both have a pixel size of 3840x2160 and a display scale of 2.0.  You can query the window display scale using `SDL_GetWindowDisplayScale()`, and when this changes you get an `SDL_EVENT_WINDOW_DISPLAY_SCALE_CHANGED` event.