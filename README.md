# yapt
Yet another pomodoro tool.

## overview
A simple pomodoro tool as simple as a bash script.
My initial intention was to use something like: https://github.com/gingivitis/i3-pomodoro, but I was discouraged due to node.
So, I decided to write a script that just uses shell and has no other requirements.

## features

- toggle
- reset 
- tick sound (optional)
- desktop notifications (optional)
- i3 integration (optional)

## usage

To simply start a timer:

    yapt

To toggle the timer (activate/deactivate):

    yapt -t

To rest the timer:
   
    yapt -r
    
To mute/unmute the tick sound:

    yapt -m 

### i3 integration

Just copy the the i3yapt from `bin/i3yapt` to your path and add the following lines, in your `i3blocks.conf`:

      [yapt]
      command=yapt
      signal=2
      interval=1
      
Actions:

- Left click: Activate/Deactivate count down (pause/resume). 
- Middle click: Reset the timer.
- Right click: Mute unmute the tick sound.

### desktop notifications

If notify-send is found in the path, it will be used to send out a notification upon completion of the pomodoro.
You can then configure you notification daemon, on how to handle the event. 
Below is an example of how to configure dunst, so that it plays a sound.

    [pomodoro_completed]
    summary = "Pomodoro Completed"
    script = mplayer /usr/local/share/sounds/completion.wav > /dev/null
    
Note: The `/usr/local/share/sounds/completion.wav` is imaginary. You should point it to where you've stored the wav file that indicates completion.
