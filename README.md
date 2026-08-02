# Sound Design Portfolio — The Ou Café / Ouppps / Dear Friend

> **Repo description (for GitHub "About"):**
> Interaction-driven sound design for three exhibition installations — The Ou Café, Ouppps, and Dear Friend — built around a no-idle-audio, interaction-only sound policy for a shared exhibition space.

Sound design work for three interactive exhibition pieces, created for a shared exhibition space with strict sound constraints: no continuous music, no idle/waiting-screen audio, and sound triggered only through active visitor interaction. Subtle environmental ambience is used sparingly, only where it doesn't dominate the shared space.

---

## Thé Ou Café

An interactive installation structured around **4 seasons**, each made of **2 linked scenes**: a *bike scene* and a *tree scene*. The two scenes within a season share the same ambient bed, so the seasonal mood carries through the whole loop without ever repeating a fixed music track.

### User Journey
- **Entry** — visitor begins in the bike scene.
- **Interaction** — pedaling / riding; the visitor decides how long to stay in this state.
- **Change** — when the visitor stops pedaling for long enough, the scene transitions from bike → tree.
- **Interaction (tree scene)** — the visitor fills a cup, which drives the length of the story being told.
- **Exit / loop** — the story concludes and the piece resolves into the next season, or ends on the Summer scene.

### Interaction Map
| User action | System response | Sound |
|---|---|---|
| Click / press bell pad | Screen zooms in/out | `bell_1_user_interaction`, `bell_2_user_interaction` |
| Riding the bike | Ambient season bed plays | seasonal ambience (rain / wind / birds / cicadas) + `bike_bell`, `pedal`, `footstep` |
| Filling the cup | Story/narration advances | `telling_the_story_composition_1`, `conversation_composition_2` |
| Reaching the final (Summer) scene | Slow zoom-out, experience ends | `the_end_composition_3` |

### Atmosphere by Season
- **Autumn** — rain
- **Winter** — wind
- **Spring** — birds
- **Summer** — cicadas (this scene runs longer — the zoom-out is slower and always completes, so it also carries the game's ending)

Each ambient bed is a ~30-second loop, designed to fade out naturally rather than cut off abruptly if a scene ends early.

### Music Cues
| Timestamp | Cue | Function |
|---|---|---|
| 2:01–2:53 | M1 — *A Brief History* | Telling the story (bike scene narration) |
| 2:54–3:59 | M2 — *Afterglow* | Conversation (background character explanation) |
| 5:12–5:47 | M3 — *A Soft Chord* | The end |

### File Structure
```
The Ou Cafe/
└── Final/
    ├── Mix composition/
    │   ├── bell_1_user_interaction
    │   ├── bell_2_user_interaction
    │   ├── conversation_composition_2      (2:54–3:59) *
    │   ├── telling_the_story_composition_1 (2:01–2:53) *
    │   └── the_end_composition_3           (5:12–5:47)
    ├── Mix elements/
    │   ├── bike_bell
    │   ├── cup
    │   ├── footstep
    │   └── pedal
    └── Mix seasons/
        ├── rain
        ├── spring
        ├── summer
        └── winter
```
`*` = loops/repeats during the experience.

### Notes
- Bell sounds are used for screen-click / user interaction.
- Conversation cue can retrigger multiple times whenever the background character speaks.
- "Telling the story" plays specifically while the character rides the bike.
- "The end" plays only at the close of the longer (Summer) scene.
- Elements and seasonal ambience were cleaned up (volume balancing, light noise reduction, reverb).
- **Open item:** interview voice recordings are still missing from the mix.

---

## Ouppps

An interactive puzzle/object-finding experience set inside a café, structured around two visual color states — **red** and **green** — that drive which interaction sounds are triggered, plus a narrative arc bookended by a recurring main theme.

### User Journey
- **Entry** — door opens, main theme plays.
- **Interaction** — visitor selects objects / solves puzzles; visuals are colored red (beginning, 0:00–3:57) then shift to green (3:58–end) as the experience progresses, each with its own zoom in/out interaction sound.
- **Change** — wrong selections trigger a distinct "wrong button" cue; correct/puzzle interactions trigger one of six puzzle sounds so repetition doesn't feel identical.
- **Exit / loop** — background music comes in near the end, door closes, main theme returns.

### Interaction Map
| User action | System response | Sound |
|---|---|---|
| Selecting an object (correct) | Puzzle interaction plays | `puzzle_1`–`puzzle_6` (varied, not `tap`) |
| Selecting an object (wrong) | Error feedback | `wrong_button_1`, `wrong_button_2` |
| Clicking during red phase (0:00–3:57) | Zoom in/out on object, pull card | `red_zoom_in_1/2`, `red_zoom_out_1/2` |
| Clicking during green phase (3:58–end) | Zoom in/out on object, pull card | `green_zoom_in_1/2`, `green_zoom_out_1/2` |
| Door opens/closes | Marks entry/exit | `door_opens`, main theme |
| Background character talking | Simple melodic bed under dialogue | `ppl_talking` |
| Object interactions (drink, glass, rain, etc.) | Ambient/foley layer | `breaking_glass`, `cafe_inside`, `drinking`, `rain_1/2`, `rewind_1–3`, `smash_new`, `snapdown`, `tap` |

### Music Cues
| Timestamp | Cue | Function |
|---|---|---|
| 0:00–0:15 | E-piano Wurli — main theme | Opens the experience (also used at the end, with door open/close) |
| 0:32–0:58 | Zoom sound — red (low) / green (high) | Interaction feedback |
| 1:36–1:42 | Analog chime — bg music | Transition cue |
| 3:12–3:55 | "Avant chord" — people talking | Background dialogue bed |
| 6:08 / 6:41 | Background music (ending) | Closing / receipt moment |

### File Structure
```
Ouppps/
└── Final/
    ├── bg/
    │   ├── bg_music        (06:08~ / 06:41~)
    │   ├── main_theme       (0:32–0:58) *
    │   └── ppl_talking      (3:12–3:55) *
    ├── effect/
    │   ├── green_zoom_in_1, green_zoom_in_2
    │   ├── green_zoom_out_1, green_zoom_out_2
    │   ├── puzzle_1–6
    │   ├── red_zoom_in_1, red_zoom_in_2
    │   ├── red_zoom_out_1, red_zoom_out_2
    │   └── wrong_button_1, wrong_button_2
    ├── element/
    │   ├── breaking_glass
    │   ├── cafe_inside
    │   ├── door_opens
    │   ├── drinking
    │   ├── rain_1, rain_2
    │   ├── rewind_1–3
    │   ├── smash, smash_new
    │   ├── snapdown
    │   └── tap
    └── interview/
        ├── barny_the_frog
        ├── cola_bottle
        ├── croissant_plate
        ├── crossword_pencil
        ├── sonia_couper (sonia_bye, sonia_hi, sonia_noworries, sonia_objet)
        ├── sonia_full
        └── stpatricday
```
`*` = loops/repeats during the experience.

### Notes
- Main theme plays at the beginning, and again at the end with the door opening/closing (once or twice, depending on final cut).
- "People talking" plays as a simple background melody during dialogue moments.
- Background music can carry a different theme at the very end, or align with the "receipt" moment.
- Selecting an object plays a puzzle sound (6 variants available) rather than a plain tap.
- `tap` → repurposed as `wrong_button_1/2`; `snapdown` → repurposed as `puzzle_1–6`; `smash` → replaced by `smash_new`.
- Element volumes balanced/equalized; rewind sounds pitch-varied for repetition.
- Interview audio was mixed manually to compensate for poor recording quality; recommend re-recording vocals in an isolated space next time.
- **Open item:** additional FX for card/finding interactions still needed.

## Dear Friend

A screen-based, correspondence-driven experience (mail, messages, UI interactions) that shifts perspective from an on-screen view to a room-scale environment. No continuous background music — sound plays only in direct response to user interaction, in line with the exhibition's no-idle-audio constraint.

### User Journey
- **Entry** — user begins at the screen/UI view; main theme marks the start.
- **Interaction** — user clicks through mail/messages, types, receives notifications, interacts with UI elements (bins, cards).
- **Change** — perspective shifts from the screen to the surrounding room; ambience shifts accordingly.
- **Exit / loop** — room theme carries through to the end of the experience.

### Interaction Map
| User action | System response | Sound |
|---|---|---|
| Experience starts | Screen/UI view begins | `main_theme_window` (1:10–1:13) |
| Perspective shifts from screen to room | Room ambience begins | `room_theme_down` (2:59–end) |
| Opening/closing a bin (UI) | UI feedback | `bins_in` (1:39), `bins_out` (1:41) |
| Mail/card notification appears | Pop-in cue | `card_mail_pops` (2:05 & 2:42) * |
| New notification | Alert cue | `notification` (2:38) * |
| Incorrect message/action | Error feedback | `wrong_message` (1:28) * |
| Walking in the room scene | Footstep foley | `foot` (3:21–3:37) |
| Typing / clicking / ambient room life | Interaction & ambient layer | `keyboard`, `typing_sound`, `click_sound`, `computer_noise`, `bird`, `drinking`, `eating`, `effect` |

### Themes
- **Main theme** — Xylophone (dark) — plays at the start of the user journey.
- **Room theme** — Wine glass (high-pass) — plays when perspective shifts from screen to room.

### File Structure
```
Dear Friend/
└── Final/
    ├── mix_composition/
    │   ├── main_theme_window (1:10–1:13)
    │   └── room_theme_down    (2:59–ending)
    ├── mix_effects/
    │   ├── bins_in (1:39)
    │   ├── bins_out (1:41)
    │   ├── card_mail_pops (2:05 & 2:42) *
    │   ├── foot (3:21–3:37)
    │   ├── notification (2:38) *
    │   └── wrong_message (1:28) *
    └── mix_elements/
        ├── bird
        ├── click_sound
        ├── computer_noise
        ├── drinking
        ├── eating
        ├── effect
        ├── keyboard
        └── typing_sound
```
`*` = loops/repeats during the experience.

### Notes
- `main_theme_window` plays before/at the beginning of the user journey.
- `room_theme_down` marks the perspective change from screen to room and carries the background melody from there.
- Bin in/out sounds can be swapped for standard UI sounds if preferred.
- Elements retouched for volume balance, light noise reduction and reverb.
- Scene was still in progress at time of mixing, so final theme placement may need revisiting — additional files can be sent for scoring once the scene is locked.
- No interview/voice recordings needed for this project (no real voice recordings used).
- Reference links: [head-md-care demo](https://js3000000.github.io/head-md-care/), [YouTube reference](https://www.youtube.com/watch?v=ya9sq1jCNZ4)

---

## Credits
Sound design: Gold Kim
Exhibition sound constraints and project structure developed in collaboration with the project teams.
