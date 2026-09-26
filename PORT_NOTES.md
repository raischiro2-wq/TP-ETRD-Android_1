# Port notes

The supplied ETRD.dll imports `dMeter2Draw_c::drawPikari` and its pre-hook callback changes the first float argument by reflecting it inside the active message-screen horizontal span.

Recovered operation:

    relative = x - screen[0xBC];
    if (0 <= relative <= screen[0xCC])
        x = screen[0xBC] + screen[0xCC] - relative;

This is the native fix required for the yellow Pikari/glow to follow the mirrored RTL text. Changing the `.blo` pane alone does not reproduce this behavior.
