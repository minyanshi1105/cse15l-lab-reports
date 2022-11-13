# Minyan Shi's CSE 15L Week 7 Lab Report
---
# Part 1
---
**Adding a new line to print before File[] paths = f.listfiles()**
Sequence of `vim` commands:<br />
/ File[] paths = f.listFiles() <enter> O System.out.println(f.toString + "is a directory"); <esc> :wq <br />
1. `/ File[] paths = f.listFiles()` `<enter>`
<img width="641" alt="Screen Shot 2022-11-10 at 11 11 56 PM" src="https://user-images.githubusercontent.com/114315303/201501533-bc1b1582-1bb9-4af2-a1ee-376f75d62814.png">
The `/` command means to search the given pattern fellowed right after, which is "File[] paths = f.listFiles()" in this given situation. And we hit <enter> to run this search command which will move the mouse to the first searching result. 
<br />
<br />
2. `O`
<img width="678" alt="Screen Shot 2022-11-10 at 11 14 28 PM" src="https://user-images.githubusercontent.com/114315303/201501779-dd8cd084-d98a-4abd-adb9-f60fcda2332b.png">
The `O` (upper case o) command append (open) a new line above the current line, automaticly enter the insert mode. As we can see there is a `-- INSERT --` indication at the bottom.
<br />
<br />
  
3. `System.out.println(f.toString + "is a directory");`
<img width="629" alt="Screen Shot 2022-11-10 at 11 16 19 PM" src="https://user-images.githubusercontent.com/114315303/201501949-40c8c2e2-5eec-4d84-ae31-a3ddad52f715.png">
Since we already in the insert mode, we may just type in what we want to add. 
<br />
<br />
  
4. `<esc>`
<img width="655" alt="Screen Shot 2022-11-11 at 2 34 09 AM" src="https://user-images.githubusercontent.com/114315303/201501981-47ecc554-7337-462e-b0ed-56ed4023aa27.png">
We hit `esc` to quit insert mode and return normal mode. As we can see the `-- INSERT --` indication at the bottom is gone.
<br />
<br />
  
5. `:wq`
<img width="803" alt="Screen Shot 2022-11-11 at 2 34 43 AM" src="https://user-images.githubusercontent.com/114315303/201502042-cb556813-e21b-445b-a5dc-12afff489864.png">
The `:wq` command means to save the changes and quit. We can now see the added line `f.toString + "is a directory"` shows up in the actual file.
<br />
<br />
