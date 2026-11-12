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
- **Visualization:** each note draws a glowing curve between positions on a circle of digits. The current chord lights up as a shape joining its notes, and every finished curve leaves a faint trace, so a fingerprint of the number builds up over time.

## Numbers

π, e, φ, √2, √3, ln 2, the Euler–Mascheroni constant γ, Catalan's constant, 1/7, 1/97, the Fibonacci numbers and the primes written in a row, or your own input (a fraction like `22/7`, a decimal like `2.5`, or any digit string).

All constants are computed exactly in the browser with `BigInt` arithmetic (1000 digits each, verified against mpmath). Real numbers can be played in any base from 2 to 12.

## Controls

Scale (major, minor, Dorian, Lydian, pentatonic, minor pentatonic, chromatic), key, tempo, hold repeats, smooth melody, phrasing, chords, bass, chord rhythm, chord root rule and volume. Press <kbd>Space</kbd> to play or pause.
