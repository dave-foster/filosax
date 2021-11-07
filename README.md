## The Filosax Dataset

**Introduction:**
The Filosax dataset was conceived, curated and compiled by Dave Foster (a PhD student on the AIM programme at QMUL) and his supervisor Simon Dixon (C4DM @ QMUL). It was introduced at [ISMIR 2021](https://ismir2021.ismir.net).

The dataset is a collection of 48 multitrack jazz recordings, where each piece has 7 corresponding audio files:

1) `Bass_Drums`, a mono audio file of a mix of bass and drums

2) `Piano_Drums`, a mono audio file of a mix of piano and drums

3) `Participant 1 Sax`, a mono audio file of solo saxophone

4) `Participant 2 Sax`, a mono audio file of solo saxophone

5) `Participant 3 Sax`, a mono audio file of solo saxophone

6) `Participant 4 Sax`, a mono audio file of solo saxophone

7) `Participant 5 Sax`, a mono audio file of solo saxophone

Each piece is ~6mins, so each of the 7 stems contains ~5hours of audio.

The motivations behind the dataset, as well as the technical details of the recording and annotation pipeline, are described in the [ISMIR 2021 paper](https://www.eecs.qmul.ac.uk/~simond/pub/2021/FosterDixon-Filosax-ISMIR2021.pdf).

**Annotations:**

For each piece, there is a corresponding [`.jams`](https://github.com/marl/jams) file containing piece-level annotations:

1) Beat annotation for the start of each bar and any mid-bar chord change
2) Chord annotation for each bar, and mid-bar chord change
3) Section annotation for when the solo changes between the 3 categories:
    a) head (melody)
    b) written solo (interpretation of transcribed solo)
    c) improvised solo

For each Sax recording (5 per piece), there is a corresponding .json file containing note annotations:

`a_start_time (float)`: the time stamp of the note start, in seconds

`a_end_time (float)`: the time stamp of the note end, in seconds

`a_duration (float)`: the duration of the note end, in seconds

`midi_pitch (int)`: the quantised midi pitch

`crochet_num (int)`: the number of sub-divisions which define a crochet (always 24)

`musician (str)`: the participant ID

`bar_num (int)`: the bar number of the start of the note

`s_start_time (float)`: the time stamp of the score note start, in seconds

`s_duration (float)`: the duration of the score note, in seconds

`s_end_time (float)`: the time stamp of the score note end, in seconds

`s_rhythmic_duration (int)`: the duration of the score note (compared to crochet_num)

`s_rhythmic_position (int)`: the position in the bar of the score note start (compared to crochet_num)

`tempo (float)`: the tempo at the start of the note, in beats per minute

`bar_type (int)`: the section annotation where 0 = head, 1 = written solo, 2 = improvised solo

`is_grace (bool)`: is the note a grace note, associated with the following note

`chord_changes {int: str}`: the chords, where the key is the rhythmic position of the chord (using crochet_num, relative to s_rhythmic_position) and the value a JAMS chord annotation  (An additional chord is added in the case of a quaver at the end of the bar, followed by a rest on the downbeat)

`num_chord_changes (int)`: the number of chords which accompany the note (usually 1, sometimes >1 for long notes)

`main_chord_num (int)`: usually 0, sometimes 1 in the quaver case described above

`scale_changes [int]`: the degree of the chromatic scale when midi_pitch is compared to chord_root

`loudness_max_val (float)`: the value (db) of the maximum loudness

`loudness_max_time (float)`: the time (seconds) of the maximum loudness (compared to a_start_time)

`loudness_curve [float]`: the inter-note loudness values, 1 per millisecond

`pitch_average_val (float)`: the value (midi) of the average pitch

`pitch_average_time (float)`: the time (seconds) of the average pitch (compared to a_start_time)

`pitch_curve [float]`: the inter-note pitch values, 1 per millisecond

`pitch_vib_freq (float)`: the vibrato frequency (Hz), 0.0 if no vibrato detected

`pitch_vib_ext (float)`: the vibrato extent (midi), 0.0 if no vibrato detected

`spec_cent (float)`: the spectral centroid value at the time of the maximum loudness

`spec_flux (float)`: the spectral flux value at the time of the maximum loudness

`spec_cent_curve [float]`: the inter-note spectral centroid values, 1 per millisecond

`spec_flux_curve [float]`: the inter-note spectral flux values, 1 per millisecond

The Participant folders also contain MIDI files of the transcriptions (frame level and score level) as well as a PDF and MusicXML of the typeset solo.

**Repertoire:**



| Tune                                   | Key | Av. Tempo (BPM) | Original Soloist       | Year | Album                                |
|----------------------------------------|-----|-----------------|---------------|------|--------------------------------------|
| All The Things You Are                 |  Ab |       139       |   Stan Getz   | 1979 | Dizzy & Stan                         |
| Alone Together                         |  Dm |       145       |  Tubby Hayes  | 1972 | Live at the Hopbine                  |
| Apple Jump                             |  F  |       162       | Dexter Gordon | 1976 | Biting The Apple                     |
| Autumn Leaves                          |  Gm |       115       |  Ben Webster  | 1965 | In Copenhagen                        |
| Blues By Five                          |  F  |       122       |  Tubby Hayes  | 1956 | Changing The Jazz                    |
| Bye Bye Blackbird                      |  F  |       144       | Sonny Rollins | 1957 | Rare Radio Recordings (Miles Davis)  |
| C Jam Blues                            |  C  |       148       |  Ben Webster  | 1964 | Soho Nights Vol. 2                   |
| Come Rain Or Shine                     |  F  |       154       | Dexter Gordon | 1967 | The Monmartre Collection             |
| Cottontail                             |  Bb |       218       | Joe Henderson | 1988 | Tenor Tribute Vol. 1                 |
| Dear Old Stockholm                     |  Gm |       139       |   Stan Getz   | 1971 | Round Midnight                       |
| Dolphin Dance                          |  Eb |       125       |  Tubby Hayes  | 1967 | For Members Only                     |
| Doxy                                   |  Bb |       121       | Sonny Rollins | 1954 | Bags’ Groove (Miles Davis)           |
| For Regulars Only                      |  Db |       176       | Dexter Gordon | 1961 | Doin’ Alright                        |
| Four                                   |  Eb |       226       | Sonny Rollins | 1964 | Now’s The Time! (Alt take)           |
| Fried Bananas                          |  Eb |       181       | Dexter Gordon | 1970 | More Power!                          |
| Gone With The Wind                     |  Eb |       152       |   Stan Getz   | 1991 | People Time                          |
| Have You Met Miss Jones?               |  F  |       204       |   Stan Getz   | 1953 | The Artistry of Stan Getz            |
| Honeysuckle Rose                       |  F  |       168       |  Ben Webster  | 1944 | Sax Greats                           |
| I’ll Remember April                    |  G  |       221       |   Stan Getz   | 1958 | Stan Meets Chet                      |
| In A Mellotone                         |  Ab |       105       |  Ben Webster  | 1959 | … And Associates                     |
| In Your Own Sweet Way                  |  Am |       111       | Sonny Rollins | 1956 | Oleo (Miles Davis)                   |
| Invitation                             |  Cm |       193       |   Stan Getz   | 1975 | The Master                           |
| Isotope                                |  C  |       185       | Joe Henderson | 1964 | Inner Urge                           |
| Just Friends                           |  F  |       215       | Dexter Gordon | 1975 | Stable Mable                         |
| Lady Bird                              |  C  |       205       | Dexter Gordon | 1964 | Concert in Belgium                   |
| Milestones                             |  Bb |       160       | Joe Henderson | 1993 | So Near, So Far                      |
| Montmartre                             | Bbm |       200       | Dexter Gordon | 1969 | The Tower of Power!                  |
| Namely You                             |  Bb |       126       | Sonny Rollins | 1957 | Newk’s Time                          |
| Now’s The Time                         |  F  |       211       |  Tubby Hayes  | 1955 | Now's The Time (Dizzy Reece)         |
| Oleo                                   |  Bb |       225       |  Ben Webster  | 1972 | Live In Paris (as “I Got Rhythm”)    |
| On Green Dolphin Street                |  Eb |       215       | Sonny Rollins | 1968 | Live In Denmark                      |
| Out Of The Night                       |  Fm |       120       | Joe Henderson | 1963 | Page One                             |
| Parisian Thoroughfare                  |  F  |       194       |  Tubby Hayes  | 1964 | Tubbs’ Tours                         |
| Pennies From Heaven                    |  C  |       125       |  Ben Webster  | 1954 | King of the Tenors                   |
| Satin Doll                             |  C  |       122       |  Ben Webster  | 1970 | In Norway                            |
| Scrapple From The Apple                |  F  |       211       |   Stan Getz   | 1966 | Jazz Goes To College                 |
| Sonnymoon For Two                      |  Bb |       149       | Sonny Rollins | 1957 | Live at the Village Vanguard         |
| Soon                                   |  Eb |       196       |  Tubby Hayes  | 1961 | Tubbs in N.Y.                        |
| Star Eyes                              |  Eb |       196       |  Tubby Hayes  | 1958 | The Couriers of Jazz!                |
| Stella By Starlight                    |  Bb |       190       | Joe Henderson | 1985 | The State Of The Tenor               |
| Step Lightly                           |  C  |       112       | Joe Henderson | 1964 | The Thing To Do (Blue Mitchell)      |
| Sweet Georgia Brown                    |  Ab |       109       |  Ben Webster  | 1973 | Gentle Ben                           |
| Take The A Train                       |  C  |       157       | Joe Henderson | 1975 | Ellington Is Forever (Kenny Burrell) |
| Tangerine                              |  F  |       218       |   Stan Getz   | 1953 | More West Coast Jazz                 |
| The Rainbow People                     |  Eb |       118       | Dexter Gordon | 1969 | The Tower of Power!                  |
| There Will Never Be Another You        |  Eb |       188       |  Tubby Hayes  | 1956 | The Swinging Giant Vol. 2            |
| Three Little Words                     |  C  |       202       | Sonny Rollins | 1956 | Live in Denmark                      |
| UMMG                                   |  Db |       217       | Joe Henderson | 1991 | Lush Life                            |

**Demo:**

Download the MIDI and wav files below, and import them into your favourite DAW, to see the note transcription accuracy and tempo matching. The PDF file shows the score representation of the same passage.

<a href="Filosax Example.wav">Download Audio File</a>

<a href="Filosax Example.mid">Download MIDI File</a>

<a href="Filosax Example.pdf">Download PDF File</a>

**Try it out:**

The full dataset is undergoing final validation checks and proof-reading, and will be available soon. In the meantime, interested parties can access a subset of the dataset, Filosax Lite, which contains 5 pieces played by 2 participants, for initial experimentation. This can be found on [Zenodo](https://zenodo.org/record/5643734#.YYLQ-i2l3UI), where an request for download needs to be accompanied by a valid research motivation and institution, and agreement with the terms and conditions. Initial users of the Lite dataset will be contacted once the full dataset is available. Integration with [mirdata](https://github.com/dave-foster/mirdata/tree/filosax)\* is also pending.

The download-able data contains all of the saxophone recordings and annotations, which may be sufficient for many applications. To download the backing data, go to jazzbooks.com, where there are pre-populated "wish lists" of the required files: [Filosax Full](https://www.jazzbooks.com/mm5/merchant.mvc?&Screen=WISH&Store_Code=JAJAZZ&WishList_ID=1679) or [Filosax Lite](https://www.jazzbooks.com/mm5/merchant.mvc?&Screen=WISH&Store_Code=JAJAZZ&WishList_ID=1678). Put the purchased files into the `/Aebersold` folder, and run the appropriate script from inside the home folder and a new Python environment:

    pip install mirdata
  
    python Scripts/Compile_Backing.py -version full # (Full version)
    python Scripts/Compile_Backing.py -version lite # (Lite version)
  
which populates the `/Backing` folder with edited files, which match the versions that were used in the recordings.
 
**Feedback:**

We welcome any constructive feedback, and will collaborate when possible to encourage novel research using the dataset.

**License:**

The Filosax dataset contains copyright material and is shared with researchers under the following conditions:
1. Filosax may only be used by the individual signing below and by members of the research group or organisation of this individual. This permission is not transferable.
2. Filosax may be used only for non-commercial research purposes.
3. Filosax (or data enabling the its reproduction) may not be sold, leased, published or distributed to any third party without written permission from the Filosax administrator.
4. When research results obtained using Filosax are publicly released (in the form of reports, publications, or derivative software), clear indication of the use of Filosax shall be given, usually in the form of a citation of the following paper:

    D. Foster and S. Dixon (2021),  Filosax: A Dataset of Annotated Jazz Saxophone Recordings.
    22nd International Society for Music Information Retrieval Conference (ISMIR).

5. Queen Mary University of London shall not be held liable for any errors in the content of Filosax nor damage arising from the use of Filosax.
6. The Filosax administrator may update these conditions of use at any time. 

**Acknowledgements:**

The author is a research student at the UKRI Centre for Doctoral Training in Artificial Intelligence and Music, supported by UK Research and Innovation [grant number EP/S022694/1].

\* "mirdata: Software for Reproducible Usage of Datasets"  
Rachel M. Bittner, Magdalena Fuentes, David Rubinstein, Andreas Jansson, Keunwoo Choi, and Thor Kell
in International Society for Music Information Retrieval (ISMIR) Conference, 2019

