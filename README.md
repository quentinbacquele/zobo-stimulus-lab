# Zobo stimulus lab

Browser tools for building synthetic playback songs of the Réunion grey white-eye
(*Zosterops borbonicus*), for the HIGH and LBHB forms.

- **[Stimulus sets](https://quentinbacquele.github.io/zobo-stimulus-lab/sets.html)**:
  one click draws a ready-to-use set of four stimuli for the playback experiment, which
  you then download as a zip.
- **[Stimulus lab](https://quentinbacquele.github.io/zobo-stimulus-lab/)**: explore any
  fragment and treatment, listen, and export single stimuli.

Everything runs in your browser and nothing is uploaded. To work offline, download
`index.html` and `sets.html` into the same folder and open them.

## A set

Each set holds four stimuli. Every one is built on a song fragment drawn at random
within its form, and the two stimuli of a form never share a fragment.

| File in the zip | Fragment | Treatment |
|---|---|---|
| `original_LBHB_<fragment>.wav` | LBHB | Original |
| `original_HIGH_<fragment>.wav` | HIGH | Original |
| `maximized_HIGH_<fragment>.wav` | HIGH | Maximized, bias 2.5 |
| `attenuated_LBHB_<fragment>.wav` | LBHB | Attenuated, smooth and scale, 0% modulation kept |

- Only fragments of at least 15 notes are used (46 HIGH, 19 LBHB).
- The fragment is repeated whole until the stimulus lasts at least 60 s, so files run
  from about 60 to 68 s. Notes are 65 ms apart and repetitions 130 ms apart.
- Files are mono, 44.1 kHz, 16-bit, with the sounding parts at -20 dBFS RMS.
- `setNN.zip` unpacks to a folder `setNN` with the four WAV files and `setNN.json`, which
  records the fragments, the settings and the random seed.

Generating a set adds it to a list on the page; nothing is downloaded until you press
Download on its row. The list shows what each set contains, and any set can be deleted
from it. Each set keeps the settings it was generated with, so downloading it again
gives the identical files even after the defaults change, and a deleted set's number is
not reused. The list can be exported as a CSV file. It is stored in the browser of the
computer you use, not shared.

## Treatments

- **Original**: a pure-tone resynthesis of the recorded fragment.
- **Maximized**: the fragment is pushed toward the note types specific to its form.
  Bias 0 leaves it untouched. Each step of bias multiplies the share of every note type
  by how many times more the form uses it than the other form. The least specific notes
  are replaced first, by notes of the same form borrowed from other fragments, and at
  high bias almost everything becomes the form's most specific type.
- **Attenuated**: same notes, with less frequency modulation inside each note, either by
  smoothing and scaling the contour or by rebuilding it from its first principal
  components. Optionally every note is moved to the fragment's average pitch.

## Data

The pages embed the dominant-frequency contours of 5,903 notes (750 fragments, 62 birds)
together with their note types, the note-type usage of each form, and the contour
principal components. They contain no audio recordings: every sound is a pure tone that
follows a contour, with fixed gaps and raised-cosine fades.

The note types and the principal components come from an analysis that is in
preparation for publication (Bacquelé et al.). Please get in touch before reusing the
data.

## Status

Working draft for field playback experiments. Questions and problems: open an issue.
