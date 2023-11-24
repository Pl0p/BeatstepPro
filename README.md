# Beatstep_Q
**Beatstep_Q** is a **MIDI Remote Script** for **Ableton Live 9, 10 & 11** and the **Arturia BeatStep** controller.  
It turns your BeatStep into a fully-fledged control-surface for Ableton Live !

- there are 6 different layers that give you a lot of control over Ableton Live:  
  - play midi instruments with access to the **full range** of midi-notes!
  - browse Ableton's library (in the info-bar) and prelisten/load/hotswap instruments & devices
  - control tracks/scenes and clips
     - select / arm / mute / solo / start / stop / record / delete / duplicate / overdub / undo / redo / ...
  - initialize and edit 16 note MIDI-sequences
     - change properties of one or more notes simultaneously via the "multi-touch" editing mode
  - get indications on the status of clips, tracks, playback-state and MIDI notes via button-LED's
  - ... and much more!

### Comments / suggestions / bugs?  
> Just drop an [Issue](https://github.com/raphaelquast/beatstep/issues) or start a [Discussion](https://github.com/raphaelquast/beatstep/discussions) and I'll see what I can do!  
  

... and as you might imagine...  
developing and maintaining all of this is quite some work, so if you like what I did, how about buying me a coffee?   

<center>
<a href="https://www.buymeacoffee.com/raphaelquast" target="_blank"><img src="https://www.buymeacoffee.com/assets/img/custom_images/yellow_img.png" alt="Buy Me A Coffee" style="height: 41px !important;width: 174px !important;" ></a>
</center>

# Installation

No real installation required... just copy the files, and you are ready to go!

1) copy all files of the latest [release](https://github.com/raphaelquast/beatstep/releases) into a folder named **"Beatstep_Q"**   
   inside the MIDI Remote scripts folder of Ableton Live   
   (located at `..install-dir..\Resources\MIDI Remote Scripts`) 
2) start Ableton and select **Beatstep_Q** as control-surface in the MIDI-tab of the preferences.  
   (make sure to activate both `track` and `remote` for this device!)

❗BeatStep's **storage bank 9** is used during runtime. Any configuration stored to this slot will be overwritten❗ 

# Overlay
The overlay-design provides indications for all assignments (including secondary-functions)  
<sup>
(I got mine printed here: [Taktility](https://www.taktility.com/))
</sup>

<table><tr>
<td align="center" width=54%>
  <img src=/BeatStep_Q_Overlay.png/>
</td>
<td align="center" width=46%>
  <img src=https://github.com/raphaelquast/beatstep/assets/22773387/829309ee-d57e-437b-81fe-b00c239b7fa0 />
</td>
</tr>
</table>


# Summary of Assignments

![assignments-image](/assignment_01.png)

---

# More detailed explanations on the assignments:

The script will set all encoders and buttons to send messages on the Midi-channel 10.  To indicate a successful setup, the top-row will light up red and blue (about 2 seconds after plugin).

- It's best to **connect the controller after Ableton started** to ensure that all settings are properly assigned.

- To ensure that the script is automatically selected (instead of the default script), rename the already existing *"Beatstep"* folder to *"_Beatstep"* (or something that it is alphabetically sorted **after** *"BeatStep_Q"*)

> After initialization, you can recall any saved MIDI configuration and the control-layers will still work!






## General (click to expand)

<details><summary>:black_square_button: <strong>BUTTONS</strong></summary>

The buttons `recall`, `store`,`chan` and `shift` are used to activate the control-layers.

- to maintain the initial functionality of the buttons, the layers are activated when the buttons are **released** !

- all layers (except the *"shift-layer"*) remain activated until the corresponding button is pressed again

- holding `shift` and pressing `chan` will activate the *"mix-layer"* 
- holding `shift` and pressing `recall` will activate the *"browser-layer"* 

- **double-tapping** `shift` will activate the *"shift-layer"* permanently (until shift is pressed again) 

- the *"if shift pressed"* features are only available if the corresponding layer is activated permanently **and** `shift` is pressed

The `stop` button works the same (on all layers) as follows:

- if the selected clip is currently recording: only recording is stopped (but playback is continued)

- if the selected clip is playing: stop is triggered

- *"if shift pressed"* : stop **ALL** tracks

> While no layer is active, all buttons can be used to play midi-notes!  
> (>> use the `transpose-encoder` to change the assigned range of midi-notes)


</details>


---

<details><summary>:white_circle: <strong>ENCODERS</strong></summary>  

The `transpose-encoder` can be used to transpose the note-assignments of the buttons.  
(a red button-color indicates that the lower-left button is at the note C-2, C-1, C0, C1, etc.)
> The info-message also tells you the current assignment of the lower-left button (e.g. `button 9`)

- `encoder 1-4` and `9-12` : control the first 8 parameters of the selected device

- `encoder 5, 6, 13, 14` : send A, B, C, D of selected track

- `encoder 7` : volume of selected track
  
  - *"if shift pressed"*: volume of master-track

- `encoder 15` : pan of selected track
  
  - *"if shift pressed"*: pan of master-track

- `encoder 8` : track-selection (left-right) [💡 this is the same for all layers!]
  
  - *"if shift pressed"* **and** a *"drum-rack"* is selected:

    select drum-pad slot of the viewed 16 slots

- `encoder 16` : scene selection (up-down) [💡 this is the same for all layers!]
  - *"if shift pressed"* **and** a *"drum-rack"* is selected:

    select row of viewed drum-pads

</details>

--- 	

## Layers (click to expand)


<details>
<summary>:trumpet: <strong>SHIFT</strong></summary>  

If NO other layer is activated, pressing "shift" temporarily activates the `shift` layer 
It serves as a *quick-access* layer for frequently used functions.  
The layer is deactivated as soon as `shift` is released!   
**double-tap** `shift` to activate the layer permanently.


The lights in the first indicate the currently activated clip.
(`red` for midi, `blue` for audio and `magenta` for return tracks)

The lights in the second row indicate the track-arm status:

- `red` if the track is **armed** and **not muted**
  
  - `magenta` if the track is armed but muted

- `blue` if the track represents a **track-group**

- `off` if the track is muted and **not** armed


#### The assignments are as follows:

- `button 1-7`: select track 1-7 of the currently focussed slots (red box)
  
  - double tap an already selected track to arm/unarm it
    - if the selected track is a track-group, instead fold/unfold the group

- `button 8`: select previous scene (e.g. go 1 scene up)
  
  - if the control-layer is activated permanently, holding `shift` will switch to track-selection

- `button 9` : undo last step

- `button 10`: delete selected clip

- `button 12`: duplicate the currently selected clip and set the focus to the duplicate

- `button 13`: duplicate the currently selected loop

- `button 15`: start recording
  
  - if the currently selected slot is empty, start recording a new clip
  
  - if a clip is already present, toggle overdubbing the clip

- `button 16` : select next scene (if at the end, create a new scene)
  
  - if the control-layer is activated permanently, holding `shift` will switch to track-selection

All encoders are assigned as described above except for the `transpose-encoder`, which is now used to **select devices** in the device-chain of the selected track. (turning the `transpose-encoder` will automatically focus the view to the device-chain!)

</details>

---

<details>
<summary>:open_file_folder: <strong>BROWSE</strong></summary>  
The browser works ONLY in the info-bar... it is not connected to Ableton's browser-window!
(I know this would be nice... but the Ableton python-API does not allow it)
The status-bar symbols indicate the following:

- :red_circle: : the selected item can be loaded
- :fire: ... :fire: : hotswap is active
- :arrows_counterclockwise: : the item can be hotswapped
- :black_circle: : the item can not be loaded directly (it's a collection of sub-items)
- :file_folder: : the item is a folder (and can not be loaded directly)
- :small_blue_diamond: a loadable item that is not selected

Most button-lights are simply there to help remember the button-assignments.
- `button 13` indicates if **hotswap** is on or off (`red` for on)
- `button 14` indicates if **prelisten** is on or off (`blue` for on)

#### The assignments are as follows:

- `button 1` : open **sounds**
- `button 2` : open **drums**
- `button 3` : open **instruments**
- `button 4` : open **audio-effects**
- `button 5` : open **MIDI-effects**
- `button 6` : open **samples**
- `button 7` : open **collections**
- `button 8` : select previous track
   - "if shift pressed" : select previous device

- `button 9` : go 1 item left
- `button 10` : go 1 item right
- `button 11` : go 1 folder-level down (if possible)
- `button 12` : go 1 folder-level up (if possible)
- `button 13` : toggle hotswapping the currently selected instrument/device
- `button 14` : toggle item-preview
- `button 15` : load the selected item (on the currently selected track if possible)
   - "if shift pressed" : load the selected item on a new track
- `button 16` : select next track
   - "if shift pressed" : select next device


All encoders are assigned similar to the *"shift-layer"*.


</details>

--- 

<details>
<summary>:violin: <strong>CONTROL</strong></summary>  

Most lights are simply there to help remember the button-assignments.
The lights of `button 13` and `button 14` indicate the status of their corresponding parameter in Live.

- `button 13` indicates the status of the metronome (`red` for on)
- `button 14` indicates the status of "automation arm" (`red` for active)
   - "if shift pressed" and an automation has been overridden, the button will turn `blue`

- `button 3`, `10` and `11` will turn red if shift is pressed to highlight the alternative functionality

#### The assignments are as follows:

- `button 1` : redo last step

- `button 2` : fold / unfold selected device

- `button 3` : activate / deactivate selected device
  
  - *"if shift pressed"* : delete selected device

- `button 6` : cycle through the *"launch-quantization"* times (e.g. 1 bar, 1/2 bar, 1/8 bar etc.)
  
  - *"if shift pressed"* : turn *"launch-quantization"* off

- `button 7` : toggle between showing the selected *"clip-details"* or the *"device-chain"* of the selected track
  
  - *"if shift pressed"* : toggle between Ableton's session-view and arrangement-view

- `button 8` : select previous scene (e.g. go 1 scene up)

- - *"if shift pressed"* : select previous track

- `button 9` : undo last step

- `button 10` : duplicate selected track
  
  - "if shift pressed" : delete selected track

- `button 11` : duplicate selected scene
  
  - *"if shift pressed"* : delete selected scene

- `button 12` : tap tempo

- `button 13` : toggle metronome

- `button 14` : toggle *"session automation record"*
  
  - *"if shift-pressed"* and an automation has been overridden: *"re-enable automation"*

- `button 15` : change the assigned "pad velocity curve" (e.g. the midi velocity response of the pad)
  
  - `blue` for linear, `magenta` for logarithmic, `red` for exponential and `off` for "always max. velocity"

- `button 16` : select next scene (if at the end, create a new scene)
  
  - *"if shift-pressed"*: select next track

All encoders are assigned similar to the *"shift-layer"*.

</details>

---

<details>
<summary>:guitar: <strong>LAUNCH</strong></summary>  

In this control-layer, both button-rows (e.g. `1-7` and `9-15`) represent clip-slots.  
NOTICE: the `stop` button has a special feature in this layer (see below).

There are 2 possible ways to activate this layer:

- tap `store` to control **2 clip-slots of 7 tracks**
   - only the `store` button LED will be on
- tap `shift + store` to control **14 clip-slots of 1 track**
   - the LED's of `store`, `chan` and `recall` will be on

The button-lights indicate the status of the clip-slots, e.g.:

- `blue` indicates a slot with a clip
  - a `blue blinking` slot indicates a clip that is triggered to **stop**

- `red` indicates a clip that is playing
  - a `red blinking` slot indicates a clip that is triggered to **play**

- `magenta` indicates a group-track (it will turn `red` if a clip of the group is playing) [or indicate a triggered clip in `shift + store` mode]

- the `shift` button indicates if *"re-trigger clips"* or *"stop clips"* mode is active

#### The assignments are as follows:

- the `stop-button` toggles the behavior of the buttons (indicated by the `shift` button LED)
  
  - *"re-trigger clips"* mode (`shift` LED OFF) : tapping on an already playing clip will **re-trigger** the clip
  
  - *"stop clips"* mode (`shift` LED ON) : tapping on an already playing clip will **stop** the clip
  
  (... the *"if shift-pressed"* behavior is still similar to the other layers, e.g. *"stop all clips"*)

- `button 1-7` : launch the clips present in the top-row of the selection.
  
  - *"if shift-pressed"* : select the track to which the clip-slot belongs to
    - if the slot is a "group-slot": fold/unfold the corresponding group

- `button 8` : select previous scene (e.g. go 1 scene up)
 
  - *"if shift-pressed"*: select previous track

- `button 9-15` : same as `1-7` but for the bottom row of the selection.

- `button 16` : select next scene (if at the end, add a new scene)
  
  - *"if shift-pressed"*: select next track

All encoders are assigned similar to the *"shift-layer"*.

</details>

---

<details>
<summary>:headphones: <strong>MIX</strong></summary>  

The lights in the top-row indicate the mute / solo status of the corresponding track.

- `blue` for a track that is set to solo

- `magenta` for an unmuted track

- `red` if the track is both solo and muted

- `off` if the track is muted and not solo

The lights in the bottom-row indicate the arm status of the corresponding track.

- `red` if the track is armed

- `blue` if the track represents a track-group

- `off` if the track is unarmed (and no track-group)

#### The assignments are as follows:

- `button 1-7` : set the **mute** status of the first 6 tracks in the red box
  
  - *"if shift pressed"*: **solo** the corresponding track

- `button 9-15` : set the **arm** status of the first 7 tracks in the red box
  
  - if the track represents a group, fold / unfold the corresponding group

- `button 8` : select previous scene (e.g. go 1 scene up)
  
  - *"if shift pressed"*: select previous track

- `button 16` : select next scene (if at the end, create a new scene)
  
  - "if shift pressed" : select next track

- `encoder 1-7` : *"track volume"* of corresponding track
  
  - *"if shift pressed"* : *"send A"* of corresponding track

- `encoder 9-15` : *"track pan"* of corresponding track
  
  - *"if shift pressed"* : *"send B"* of corresponding track

- `encoder 8` : track-selection (left-right)

- `encoder 16` : scene selection (up-down)

- `transpose encoder` : set volume of master-track

</details>

---

<details>
<summary>:musical_score: <strong>SEQUENCER</strong></summary>  

The `sequencer`-layer is only available in **Ableton 11** or newer!  

The `sequencer` layer has 2 different functionalities:

- If `shift` is pressed, you can use all button-functions from the `shift`-layer!


NOTE: The first 6 characters of a clip-name are used to parse the tempo of the midi sequence!  
> E.g. a clip-name starting with `1/32_Q` will be identified as having a tempo of 1/32.  
> Any characters after the first 6 are ignored. (e.g. a name of `1/32_Q what a nice clip` is fine!)


<details>
<summary>:ant: <strong>SEQUENCE EDITOR</strong> (active if a MIDI clip is selected)</summary>  

In the sequence-editor mode you can edit the first 16 notes of the selected MIDI clip.

- the colors of `buttons 1-16` are
  - `black` if there is no note or the note is muted
  - `blue` if there is a note, and it is unmuted
  - `magenta` if the note is unmuted and outside the loop
    - it also indicates if less than 16 notes are present
  - a moving `red` light indicates the playback-state of the clip

- check the Ableton info-bar for info-messages!

#### The assignments are as follows:

- multi-touch editing mode:
   - touch & hold one (or more) buttons and turn the `transpose`-encoder to change the assigned property of the selected notes
   - use `encoder 1-6` to set which property you want to change

- `button 1-16` : mute/unmute corresponding note
- `shift` + `button 1-16` : use functionality of `shift`-layer

- `encoder 1` : set encoders to change **note pitch**
- `encoder 2` : set encoders to change **note velocity**
- `encoder 3` : set encoders to change **note start-time**
- `encoder 4` : set encoders to change **note duration**
- `encoder 5` : set encoders to change **note velocity-deviation**
- `encoder 6` : set encoders to change **note probability**

- `encoder 8` : select prev/next track

- `encoder 9` : change the loop start-time (coarse steps)
- `encoder 10` : change the loop start-time (fine steps)
- `encoder 11` : change the position of the loop (fine steps)
- `encoder 12` : change the loop end-time (fine steps)
- `encoder 13` : change the loop end-time (coarse steps)

- `encoder 15` : transpose all notes that are inside the loop
- `encoder 16` : select prev/next scene

- `shift` + `encoder 1-16` : change assigned parameter of corresponding note

</details>


<details>
<summary>:hatching_chick: <strong>SEQUENCE INITIALIZER</strong> (active if the selected clip-slot is empty)</summary>  

In the sequence-initializer layer you can set the start-parameters for the midi-sequence  
that is initialized if you press `chan` again.

- `buttons` 1-8 indicates the tempo of the MIDI notes as "notes/bar"
  [1/32, 1/16, 1/8, 1/4, 1/2, 1, 2, 4]

- `buttons` 9, 10, 11, 12 indicate how the note-interval is filled
  - NOTE you can also use this to offset the notes!
- `buttons`13, 14, 15, 16 indicate the velocity of the notes (0.25, 0.5, 0.75, 1)

- check the Ableton info-bar for info-messages!

#### The assignments are as follows:

- `buttons` 1-8: set sequence-tempo
- `buttons` 9, 10, 11, 12 : set note-interval
- `buttons`13, 14, 15, 16 : set velocity
- **double-tap** `shift` : initialize a 16 note midi sequence with the selected parameters

- `transpose-encoder` : set the note-pitch for the initialized sequence

- `encoder 1` : set encoders to change **note pitch**
- `encoder 2` : set encoders to change **note velocity**
- `encoder 3` : set encoders to change **note start-time**
- `encoder 4` : set encoders to change **note duration**
- `encoder 5` : set encoders to change **note velocity-deviation**
- `encoder 6` : set encoders to change **note probability**

- `encoder 8` : select prev/next track

- `encoder 9` : set pitch increment of notes
- `encoder 10` : set number of incremented notes

- `encoder 15` : transpose all notes that are inside the loop
- `encoder 16` : select prev/next scene

</details>


</details>
---  

## Thanks to

- [untergeek](https://www.untergeek.de/2014/11/taming-arturias-beatstep-sysex-codes-for-programming-via-ipad/) for unravelling BeatStep sysex messages

- Julien Bayle for the awesome [PythonLiveAPI_documentation](https://julienbayle.studio/PythonLiveAPI_documentation/) and some more info's ( [here](https://julienbayle.studio/ableton-live-midi-remote-scripts/) )

- Hanz Petrov for his [Introduction to the Framework-classes](https://livecontrol.q3f.org/ableton-liveapi/articles/introduction-to-the-framework-classes/) and the corresponding [remotescripts-blog](http://remotescripts.blogspot.com)

---
 
