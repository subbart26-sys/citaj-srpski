# AUDIT v68

## Main changes
- Removed verb-form card and remote verb lookup from the word popup.
- Verb forms remain in the dedicated Tense Trainer; no trainer functionality was removed.
- `getTranslation()` now uses O(1) verb indexes instead of `findVerbInfo()` full scans.
- Remote lemma refinement is deferred with `setTimeout`, so the immediate save path is local and non-blocking.
- Word saving still stores the word in the general vocabulary and, when opened from a text, links it to that text.

## Expected result
- Clicking a verb in a text no longer performs verb-form analysis or opens the three-form verb card.
- Saving a word should be substantially faster on mobile.
- Tense Trainer continues to contain the dedicated verb database and tense forms.

## Future audit notes
- Consider a proper Serbian morphological lemmatizer if broader case/number/gender coverage is needed.
- Keep text-to-word links independent of SRS so learned words remain attached to their source text.
