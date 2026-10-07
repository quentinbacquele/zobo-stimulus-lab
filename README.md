# Zobo stimulus lab

A browser tool for building synthetic playback songs of the Réunion grey white-eye
(*Zosterops borbonicus*), for the HIGH and LBHB forms.

**Open it: <https://quentinbacquele.github.io/zobo-stimulus-lab/>**

The page has two parts:

- **Stimulus lab** (top): explore any fragment and treatment, listen, and export single
  stimuli.
- **Stimulus sets** (bottom): one click draws a ready-to-use set of four stimuli for the
  playback experiment, which you then download as a zip.

Everything runs in your browser and nothing is uploaded. To work offline, download
`index.html` and open it.

## A set

Each set holds four stimuli, in a random order: the order in which to play them. Every
stimulus is built on a song fragment drawn at random within its form, and the two
stimuli of a form never share a fragment.

| Stimulus | Fragment | Treatment |
|---|---|---|
| Original LBHB | LBHB | Original |
| Original HIGH | HIGH | Original |
| Maximized HIGH | HIGH | Maximized, bias 2.5 |
| Attenuated LBHB | LBHB | Attenuated, smooth and scale, 0% modulation kept |

- Only fragments of at least 15 notes are used (46 HIGH, 19 LBHB).
- The fragment is repeated whole until the stimulus lasts at least 60 s, so files run
  from about 60 to 68 s. Notes are 65 ms apart and repetitions 130 ms apart.
- Files are mono, 44.1 kHz, 16-bit, with the sounding parts at -20 dBFS RMS.
- `setNN.zip` unpacks to a folder `setNN` with the four WAV files and `setNN.json`, which
  records the fragments, the order, the settings and the random seed. Files are named
  `<place>_<treatment>_<FORM>_<fragment>.wav`, for example
  `2_maximized_HIGH_ZB_0025_211109_015.WAV_24.wav`, so they sort in playing order.

### Using the sets

- **New set** draws four stimuli and adds the set to the row of numbered buttons. Nothing
  is downloaded at that point.
- **The numbered buttons and the arrows** move between sets; one set is on screen at a
  time. A dot on a button shows that the set has notes (orange: some playbacks, green:
  all four).
- **Download sounds**, on a set, saves its four WAV files as `setNN.zip`. Each set keeps
  the settings it was generated with, so its sounds are identical every time, even after
  the defaults change.
- **Date, hour and coordinates** of the session are noted once per set, above its
  playbacks. "Now" fills in the current date and hour, "Use my position" the coordinates
  of the device, and pasting `latitude, longitude` into either box fills both.
- **Each row is one playback**, in playing order, with a button to hear the stimulus and
  a small chart of one fragment (notes coloured by type). Clicking its name opens it in
  the lab above.
- **Next to each playback are the fields to fill in afterwards:** time spent within 1 m
  (minutes and seconds), the largest number of birds seen within 1 m, 2 m and 5 m, and
  comments. They are saved as you type.
- **Delete this set**, at the bottom of a set, removes it and its notes. A new set takes
  the lowest free number, so the numbers of deleted sets are used again; the creation
  time and seed in `setNN.json` tell two sets with the same number apart.

### Your data

Everything is stored in the browser of the computer you use: not online, and not shared
with anyone.

- **Download data** saves `playback_data_<date>.csv`, one row per playback for every
  set: set, order, file name, treatment, form, the date, hour and coordinates of its
  set, time spent within 1 m (as m:ss and in seconds), the three counts and the
  comments, followed by how the stimulus was made.
  The page tells you whether anything changed since the last download.
- **Import data** reads such a file back, on any computer. Sets that are already there
  get the notes of the file; other sets are added, under a new number if theirs is
  taken. A file re-saved from a spreadsheet with semicolons is accepted too.
- **Clear all** removes every set and its notes from the browser.

Download the data regularly: it is the only copy outside the browser.

## Treatments

- **Original**: a pure-tone resynthesis of the recorded fragment.
- **Maximized**: the fragment is pushed toward the note types specific to its form.
  Bias 0 leaves it untouched. Each step of bias multiplies the share of every note type
  by how many times more the form uses it than the other form. The least specific notes
  are replaced first, by notes of the same form borrowed from other fragments, and at
  high bias almost everything becomes the form's most specific type.
- **Attenuated**: the fine structure of the fragment is reduced. *Smooth + scale* smooths
  each note's contour and shrinks its frequency modulation (down to a flat tone at 0%);
  *PC reconstruction* rebuilds each note from its first principal components. Two boxes
  can be ticked on top: *Same pitch for all notes* moves every note to the fragment's
  average pitch, and *Fill silences (whistle)* replaces each silence between two notes
  by a straight pitch glide, so the fragment becomes one continuous whistle.

## Data

The pages embed the dominant-frequency contours of 5,903 notes (750 fragments, 62 birds)
together with their note types, the note-type usage of each form, and the contour
principal components. They contain no audio recordings: every sound is a pure tone that
follows a contour, with fixed gaps and raised-cosine fades.

The note types and the principal components come from an analysis that is in
preparation for publication (Bacquelé et al.). Please get in touch before reusing the
data.

## Staying up to date

An open or cached page checks `version.txt` when it loads and moves to the latest
published version by itself, so everyone works with the same settings. `sets.html` only
forwards old links to the sets part of the page.

## Status

Working draft for field playback experiments. Questions and problems: open an issue.
