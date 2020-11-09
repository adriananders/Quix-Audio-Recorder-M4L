<h1>User Guide</h1>

Inspired by the recording workflow of "sampling" samplers such as the SP-x0x series as well as software solutions like Beatmaker 3 on iOS, Quix is a flexible and easy to use midi-controlled audio recorder for Ableton Live 10/Max For Live 8.<br>
Since almost every parameter can be automated in Live via MIDI, Quix allows a user accustomed to hardware sampling to immediately record, trim, and save audio snippets from routed audio sources with minimal on-screen mouse usage within Ableton.<br>

<h2>Requirements</h2>
  <ul>Ableton Live 10 (tested with Live 10.1.25 on MacOS 10.14.6 Mojave)</ul>
  <ul>Max For Live 8 (made with 8.1.8 on MacOS 10.14.6 Mojave)</ul>

<h2>Usage</h2>

Add the file <a href="/devices/Quix Audio Recorder.amxd">Quix Audio Recorder.amxd</a> to your preferred Max For Live Audio Effects Path.<br>
Drag and drop the patch into an available channel as an audio effect.<br>
If using a MIDI controller, open Ableton Live's MIDI Mapping menu to specify parameter mappings for each of the UI elements.<br>
Recordings are saved in the "Temp File Path" specified in the UI.

<h2>Parameter Guide</h2>

<h4>Rec</h4>
<img src="/img/01-rec.png" alt="Rec">
If recording method is set to "Manual", begins recording immediately on click.<br>
Otherwise arms Quix to record when record method conditions are met.

<h4>Reload Rec</h4>
<img src="/img/02-reload-rec.png" alt="Reload Rec">
Resets the audio buffer to the current recorded file. Allows a user to revert trim and normalization actions, and thus "chop" a recording similar to SP-x0x from within Quix.

<h4>Threshold</h4>
<img src="/img/03-threshold.png" alt="Threshold">
Sets the "Gate" record method threshold for recording. Also displays the current input levels in other recording modes.

<h4>Gain</h4>
<img src="/img/04-gain.png" alt="Gain">
Adjusts the gain for recording and audio passthrough.

<h4>Pan</h4>
<img src="/img/05-pan.png" alt="Pan">
Adjust the audio balance for recording and audio passthrough.

<h4>Start/End</h4>
<img src="/img/06-start-end.png" alt="Start/End">
Numberboxes for setting the playback start and end in floating point ms.<br>
Range is automatically set based on current recording.<br>
Cannot be mapped to MIDI nor automated due to Max 8 limitations related to dynamic parameter range.<br>

<h4>Start/End %</h4>
<img src="/img/07-start-end-percent.png" alt="Start/End %">
Adjusts the playback start/end time in percentage.<br>
Can be mapped to MIDI for coarse start/end point adjustment.

<h4>Start/End Adj</h4>
<img src="/img/08-start-end-adj.png" alt="Start/End Adj">
Fine-tune adjustment of the playback start/end time in ms within +/- 130ms of current start/end points.<br>
Functionality is similar to SP-x0x start/end point adjustment.

<h4>Recenter Adj</h4>
<img src="/img/09-recenter-adj.png" alt="Recenter Adj">
Recenters Start/End Adj dials to their centerpoint for additional fine start/end playback adjustment.<br>
Functionality is similar to SP-x0x "Start/End" button when adjusting start/end points.

<h4>Reset Sel</h4>
<img src="/img/10-reset-sel.png" alt="Reset Sel">
Resets current playback start/end points of the current buffer.

<h4>Clear</h4>
<img src="/img/11-clear.png" alt="Clear">
Clears the current buffer.

<h4>Save As</h4>
<img src="/img/12-save-as.png" alt="Save As">
Opens up a file dialog menu for saving the current buffer as a specified file format and type.

<h4>Normalize</h4>
<img src="/img/13-normalize.png" alt="Normalize">
Normalizes the current audio buffer to 100%.

<h4>Trim</h4>
<img src="/img/14-trim.png" alt="Trim">
Trims the audio buffer to the specified start/end points.

<h4>Preview</h4>
<img src="/img/15-preview.png" alt="Preview">
Plays back the current audio buffer until either the preview button is toggled off<br>
or the end point is reached when looping is not enabled.

<h4>Loop</h4>
<img src="/img/16-loop.png" alt="Loop Off">
Turns Preview Looping on/off.

<h4>Waveform Preview</h4>
<img src="/img/17-waveform-preview.png" alt="Waveform Preview">
Visual display of the current buffer waveform.<br>
In additon playback start/end selection can be made by clicking and dragging the highlight box.

<h4>Channels</h4>
<img src="/img/18-channels.png" alt="Channels">
Specifies recording channels during recording. Stereo (default) or Mono.

<h4>Record Method</h4>
<img src="/img/19-record-method.png" alt="Record Method">
Specifies the recording method employed by Quix.
  <ul>Manual sets the record start/end to be triggered by the "Rec" button only.</ul>
  <ul>Seq sets the record start to be triggered by first "Arming" the Rec button (yellow)<br>
      then pressing "play" on Live's transport (turning Rec button red).<br>
      Recording is stopped either toggling "Rec" off manually<br>
      or by pressing "stop" on Live's transport.</ul>
  <ul>Gate sets the record start to be triggered by first "Arming" the Rec button (yellow)<br>
      then exceeding the audio recording threshold set in the "Threshold" parameter with the audio input.<br>
      Recording is stopped by toggling "Rec" off manually.</ul>

<h4>Monitor</h4>
<img src="/img/20-monitor.png" alt="Monitor">
Similar behvior to Live's channel "Monitor" settings.
  <ul>Off prevents audio from being sent out of Quix, eliminating feedback loops during recording.</ul>
  <ul>Auto only allows audio to be passed through Quix when Ableton itself is recording.</ul>
  <ul>In (recommended for sampling external sources) passes audio through Quix's audio out regardless of state.</ul>
Using Live's API, Quix bi-directionally keeps the "Monitor" settings in sync with the channel Quix is on.<br>
Changing Monitor in Quix changes the channel's Monitor settings and vice-versa.

<h4>Delay Compensation</h4>
<img src="/img/21-delay-compensation.png" alt="Delay Compensation">
To be used in conjunction with Seq recording method and "Measure" duration.<br>
A workaround to a <a href="https://cycling74.com/forums/can-i-get-the-audio-buffer-size-of-live">known defect with Ableton Live's integration with Max</a>.<br>
Delays the recording start and stop by the number of samples specified in the drop down, thus allowing for a clean perfect loop recording.

<h4>Sample Type</h4>
<img src="/img/22-sample-type.png" alt="Sample Type">
Specifies one of the Sample Types supported by Max 8.
  <ul>int8</ul>
  <ul>int16 (default)</ul>
  <ul>int24</ul>
  <ul>int32</ul>
  <ul>float32</ul>
  <ul>float64</ul>
  <ul>mulaw</ul>
  <ul>alaw</ul>

<h4>File Format</h4>
<img src="/img/23-file-format.png" alt="File Format">
Specifies either WAVE or AIFF recording.

<h4>Recording Duration</h4>
Toggles between the 4 recording duration behaviors.
<h5>Unlimited</h5>
<img src="/img/24-recording-duration-01-unlimited.png" alt="Recording Duration-Unlimited">
Completely unlimited recording saved directly to disk only stopped when toggling off on the Rec button.<br>
Please be aware of your system's hard-drive space limitations as prolonged recordings may introduce instability if available space is exceeded.<br>
<h5>Time</h5>
<img src="/img/24-recording-duration-02-time.png" alt="Recording Duration-Time">
Sets a recording time limit in Hours : Minutes : Seconds : Milliseconds (default 30). Will auto-stop recording at the time specified.
<h5>Measure</h5>
<img src="/img/24-recording-duration-03-measure.png" alt="Recording Duration-Measure">
Sets a recording time limit in Live Bars.Beats (default 1 bar). Automatically sets record method to Seq when toggled.<br>
Will auto-stop recording after the specified number of Bars.Beats have passed in the playback transport.
<h5>Position</h5>
<img src="/img/24-recording-duration-04-position.png" alt="Recording Duration-Position">
  <ul>Sets a recording start point in Bars.Beats (default 1.1), delaying the recording start until the transport reaches the specified transport point.</ul>
  <ul>Sets a recording stop point in Bars.Beats (default 1 beat) from the specified start location (default 1 beat).</ul>

<h4>Temp File Path</h4>
<img src="/img/25-temp-file-path.png" alt="Temp File Path">
Specifies a file path for temporary recordings, defaulting to the device's path. Recordings are auto-named numerically based on the system clock.

<h2>Tips, Tricks, Notes, & Recommendations</h2>
  <ul>Place Quix on its own otherwise empty audio channel, routing your project channels through it to capture audio on the fly.</ul>
  <ul>Recording files of unlimited length to disk is required per current Max limitations.<br>
      Other similar devices require a user to specify a recording length BEFORE recording. Quix is unique that it can handle unlimited recording lengths.<br>
      This is achieved through recording directly to disk rather than memory. Please be aware that over time you will need to clean out the temp file location.</ul>
  <ul>Due to current limitations with Max 8, Start and End number boxes cannot be both automated AND have dynamic value ranges.<br>
      As a result, Start and End are intentionally not mappable parameters. Map Start and End % dials to automate coarse start/end points.</ul>
  <ul>Due to a current defect with <a href="https://cycling74.com/forums/can-i-get-the-audio-buffer-size-of-live">Ableton Live's integration with Max</a> the first<br>  
      beat of every Seq synced measure duration recording will be cut off by the exact sampling buffer of Live.<br>
      This is a defect with Max and Live itself and thus can't be addressed through a bug-fix with this device.<br>
      Use the workaround provided through Delay Compensation to create perfect transport syncronized recorded loops.</ul>
  <ul>Start/End Adj controls, Recenter, Preview, Trim, Save As, and Reload Rec buttons are all designed to provide an experience similar to chopping beats<br>
      in an SP-x0x type sampler. Specifically the method detailed in this <a href="https://www.youtube.com/watch?v=N-GztP2f0Js">YouTube</a> video.<br>
      This is great to use in conjunction with a MIDI controller or Push to make for quick chopping using one's ears rather than visual or automatic chops.</ul>
  <ul>Save As does not trim the audio nor save the playback start/end points specified in the preview window.<br>
      Please apply Trim to commit the start/end to the buffer.</ul>
  
