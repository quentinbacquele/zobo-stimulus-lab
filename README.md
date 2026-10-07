# Zobo stimulus lab

A browser tool for building synthetic playback songs of the Réunion grey white-eye
(*Zosterops borbonicus*), for the HIGH and LBHB forms.

**Open it: <https://quentinbacquele.github.io/zobo-stimulus-lab/>**

Everything runs in your browser and nothing is uploaded. To use it offline, download
`index.html` and open it.

## What it does

1. **Pick a song fragment.** Only recorded fragments of at least 15 notes are offered
   (46 HIGH, 19 LBHB). The strip under the menu shows where each fragment already sits
   on the bias scale of its form.
2. **Pick a treatment.**
   - *Realistic*: a pure-tone resynthesis of the recorded fragment.
   - *Biased*: same rhythm, but the notes are redrawn from a mix that over-uses the note
     types specific to the form. Bias 0 is the form's typical mix; each step multiplies
     every type's share by how many times more the form uses it than the other form.
   - *Attenuated*: same notes, with less frequency modulation inside each note, either by
     smoothing and scaling the contour or by rebuilding it from its first principal
     components.
3. **Listen and export.** The fragment is repeated until the stimulus lasts at least
   30 s. Download the WAV (mono, 44.1 kHz, 16-bit) and a manifest with every parameter
   and source note.

## Data

The page embeds the dominant-frequency contours of 5,903 notes (750 fragments, 62 birds)
together with their note types, the note-type usage of each form, and the contour
principal components. It contains no audio recordings: every sound is a pure tone that
follows a contour, with fixed gaps (65 ms by default) and raised-cosine fades.

The note types and the principal components come from an analysis that is in
preparation for publication (Bacquelé et al.). Please get in touch before reusing the
data.

## Status

Working draft for field playback experiments. Questions and problems: open an issue.
