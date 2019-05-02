# my-st

This is my patched and custom version of st or Simple Terminal from suckless.org.

## Patches
1. [anysize](https://st.suckless.org/patches/anysize/)
2. [clipboard](https://st.suckless.org/patches/clipboard/)
3. [scrollback](https://st.suckless.org/patches/scrollback/)
4. [xresources](https://st.suckless.org/patches/xresources/)

### Scrollback
  I have all three patches so I can scrollback with my mouse alone.
  
### DEL and Backspace
After reading the comment [here](https://git.suckless.org/st/commit/f210ea26c444607980d5de17ed7d4e62bb813631.html). I kinda understood what was going on. Backspace goes back to a key but does not delete it or something crazy from the Typewriter days. To fix it all I had to do was comment out..
```c
/*	{ XK_Delete,        XK_ANY_MOD,     "\033[3~",      +1,    0}, */
```
and replace the `\033[P' here..
```c
	{ XK_Delete,        XK_ANY_MOD,     "\033[P",       -1,    0},
```
with `\033[3~` like..
```c
	{ XK_Delete,        XK_ANY_MOD,     "\033[3~",       -1,    0},
```

and now it works like expected.

## Colors and font
I set my font to [Hermit](https://github.com/pcaro90/hermit) and my colors are a custom variation of [base16 grayscale](https://github.com/chriskempson/base16-xresources/blob/master/xresources/base16-grayscale-dark.Xresources).

I also have the Xresouces patch but I have not yet used it as of writing this README.md
