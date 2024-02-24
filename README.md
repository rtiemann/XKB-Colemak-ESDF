This patch enhances XKB's US Colemak layout:

- Right Shift is Level 5 shift.
- On Level 5, the cursor keys are mapped to physical E, S, D, and F keys
  (hold right shift and use E, S, D, F as cursor keys).
- On Level 5, the Home, End, PageUp, and PageDown keys are mapped to
  physical W, R, T, and G keys.
- On Level 5, F13 through F24 are mapped to the F1 through F12 key.

Why ESDF? Because using WASD is a terrible idea. As a touch typist, your
left hand hovers over the home row with the index finger right over the
(physical) F key. Using ESDF as cursor block is much easier than using
WASD because either you'd have to use middle finger, ring finger, and
pinky to reach them (which is clumsy) or you'd have to shift your hand
one position to the left (which is even more clumsy).

Why Right Shift for Level 5? Because it is the most convenient key for
this purpose on my Laptop keyboard.

As XKB is hard to extend, the system file which defines the Colemak layout
is patched directly. It is next to impossible to add a custom layout in a
clean way, that's why I'm simply changing the existing one.
See also [The Bazaar with Landmines (or How To Extend XKb the Right Way)][1].

Files:

- `us.original`: The original file copied from my system's
  `/usr/share/X11/xkb/symbols/us` for reference. The exact path may be
  different on your machine.
- `us.esdf`: The patched file containing my changes, also just for reference.
- `us.patch`: The diff. To apply, run  
  <code>sudo patch -i us.patch /usr/share/X11/xkb/symbols/us</code>
- `us_esdf`: My layout in isolation the way I planned to add it if there was
  any sane way to accomplish this.

Note that the same result can be achieved via `xmodmap`, but it won't play
nicely when switching keyboard layouts via XKB.

[1]: https://danijozsef.medium.com/the-bazaar-with-landmines-or-how-to-extend-xkb-the-right-way-b82de59a1f9a
