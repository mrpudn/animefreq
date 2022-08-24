# animefreq

An analysis of the frequency of words appearing in Japanese anime.

## Overview

Japanese subtitles were obtained from an export of [Kitsunekko] from 4/7/2020.
Only `.srt` files were used in the analysis. All non-anime titles were filtered
out (ex. tokusatsu shows). These subtitles were run through [SudachiPy], a
Japanese morphological analyzer, to produce morphological information about each
subtitle. This morphological information is aggregated for each show and stored
in the files in the `shows/` directory. All of this morphological information is
further aggregated for all shows and stored in the `animefreq.csv` file.

Some additional filtering and processing was also performed. Some of the tokens
contained half-width kana characters - these were converted to their full-width
equivalents. Tokens containing characters other than kanji, kana, and a few
other characters were discarded.

Each show is assigned a UUID. Each file in the `shows/` directory is named using
this UUID. The Japanese and English names for each show were collected by hand
using [MyAnimeList]. All of this show information is stored in `shows.csv`.

## Field Information

### `animefreq.csv`

- `Word`: A Japanese word.
- `DictionaryForm`: The dictionary/root form of the word.
- `NormalizedForm`: The normalized root form of the word.
- `PartOfSpeech`: Part of speech information about the word.
- `Dependencies`: A space-separated list of smaller words that compose the word.
- `Count`: The number of times the word appeared.
- `Files`: The number of subtitle files in which the word appeared.

### `shows.csv`

- `UUID`: A UUID assigned to the show.
- `Japanese`: The Japanese name of the show (source: [MyAnimeList]).
- `English`: The English name of the show (source: [MyAnimeList]).
- `KitsunekkoID`: The ID (or name) of the show in [Kitsunekko].
- `MyAnimeListID`: The ID of the show in [MyAnimeList]

### `shows/<UUID>.csv`

- `Word`: A Japanese word.
- `DictionaryForm`: The dictionary/root form of the word.
- `NormalizedForm`: The normalized root form of the word.
- `PartOfSpeech`: Part of speech information about the word.
- `Count`: The number of times the word appeared.
- `Files`: The number of subtitle files in which the word appeared.

<!-- links -->
[Kitsunekko]: https://kitsunekko.net
[SudachiPy]: https://github.com/WorksApplications/SudachiPy
[MyAnimeList]: https://myanimelist.net/
