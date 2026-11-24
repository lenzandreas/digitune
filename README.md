# Digitune

Create melodies using the digits of irrational numbers, and watch them drawn as they play.

Digitune turns each digit of a number such as π, e or φ into a note, harmonizes it with chords taken from the number's own digits, and draws the melody live on a circle of digits.

## Run it

Open `index.html` in any modern browser (desktop, tablet or phone) and press **Play**. There is nothing to install or build; the app is a single self-contained HTML file using the Web Audio API and a canvas. To host it, enable GitHub Pages for the `main` branch (root folder).

## How the music follows the digits

- **Melody:** every digit is one eighth note. Digits map to steps of the chosen scale: 1 is the home note, 2 the next step up, and 0 one step below home.
- **Smooth melody:** each note keeps its name from the digit, but moves to the octave closest to the previous note (with a gentle pull toward the middle), so big jumps like 1 → 9 become small steps. On π this halves the average interval and removes all leaps wider than a fifth.
- **Phrasing and dynamics:** the first note of each group is accented, each phrase swells and settles, its last note is shorter and softer, and larger digits play a little louder and brighter. All loudness comes from the digit and its position; no notes are added.
- **Rhythm:** notes are even; a repeated digit (like the `999999` in π) is held as one longer note instead of being replayed (can be switched off).
- **Harmony:** every 4 or 8 digits, a digit of the group (the first one, or the most frequent one) becomes the chord root. The chord is a triad of the same scale, played as a soft pad with a bass note. Nothing is added that the number doesn't contain.
- **Drums:** every 8 digits (one bar of four beats), the bar's first three digits set how many kick, snare and hi-hat hits it has, and each count is spread as evenly as possible over 8 or 16 steps (a Euclidean rhythm, as found in many traditional rhythms: 3 hits over 8 steps is the tresillo). The kick starts on the downbeat and the snare sits halfway between hits, so even random digits give a steady groove. All drums are synthesized with Web Audio (oscillators and filtered noise, no samples) and follow the tempo.
- **Visualization:** each note draws a glowing curve between positions on a circle of digits. The current chord lights up as a shape joining its notes, and every finished curve leaves a faint trace, so a fingerprint of the number builds up over time. Each kick sends a soft pulse out from the circle, and the drum grid in the controls shows the current bar's pattern as it plays.

## Numbers

π, e, φ, √2, √3, ln 2, the Euler–Mascheroni constant γ, Catalan's constant, 1/7, 1/97, the Fibonacci numbers and the primes written in a row, or your own input (a fraction like `22/7`, a decimal like `2.5`, or any digit string).

All constants are computed exactly in the browser with `BigInt` arithmetic (10,000 digits each, verified against mpmath; γ takes about two seconds, the others are near-instant). Real numbers can be played in any base from 2 to 12.

## Controls

Scale (major, minor, Dorian, Lydian, pentatonic, minor pentatonic, chromatic), key, tempo, hold repeats, smooth melody, phrasing, chords, bass, chord rhythm, chord root rule, volume, drum steps (off, 8 or 16) and drum level. Press <kbd>Space</kbd> to play or pause.
