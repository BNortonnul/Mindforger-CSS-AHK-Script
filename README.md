# Mindforger-CSS-AHK-Script

## CSS DOCUMENTATION

These can be found in "CSS.zip". To utilize, do as follows:

![mindforger_VdGQI7gnFH](https://user-images.githubusercontent.com/23107982/156518034-e4e3e622-5b6f-46d4-8d3f-0bbb2e968c25.png)

![image](https://user-images.githubusercontent.com/23107982/156653526-70e30748-8fa6-4006-a0d4-0caebba4a425.png)

![mindforger_qFLZAXNIZo](https://user-images.githubusercontent.com/23107982/156518194-e98afc23-4ce5-480a-a7ff-0335d492bffa.png)

Refresh the preview to see the new CSS take effect.

Make sure to install the fonts or otherwise it will not look like these previews.

### Sentinel

Font dependencies: Ubuntu Medium, Ubuntu

Intended to provide a strong sense of header hierarchy.

![mindforger_vj9MOd1L7L](https://user-images.githubusercontent.com/23107982/156517656-2f458947-3b70-45b4-abef-50ddc66ab16f.png)

### Moderna

Font dependencies: Audiowide, Ubuntu Light

This one uses the two images included. Keep them in the same directory together.

![mindforger_go4Tkp4HIX](https://user-images.githubusercontent.com/23107982/156517681-64e25ead-204e-49f1-863b-11f2bf3dd164.png)

### Vantablack

Font dependencies: Literata Light, Playfair Display Black

![NVIDIA_Share_Xy04wZ3VNg](https://user-images.githubusercontent.com/23107982/156517779-ae5d7f43-74e3-4a33-bbbf-54fee980bf36.png)

### Toothpaste

Font dependencies: Lato, Playfair Display

![mindforger_H3IttUxPMi](https://user-images.githubusercontent.com/23107982/156517811-ae12e6d9-1dbc-4c2b-a18f-8cf8c1804fb4.png)


## SCRIPT DOCUMENTATION

This is intended to provide workarounds for various issues with mindforger. This works only on Windows, because it is programmed in AutoHotkey.

Be careful using "destructive" functions. They can blow up and destroy information if misused. Make sure to test them to determine what pace your MindForger can accept commands. On line 18, the global variable "normalDelay" is the base value which all delay commands are based off of; adjust it to whatever is appropriate for you.

### NOTE MOVEMENT FUNCTIONS

Ctrl + E: Extract all headings in a note into a series of separate notes. If there is a heading hierarchy, it will be preserved (within reason). Timestamps will be added to both the extracted-from and extracted-into notes, which are different. This can be done in either the note editor, or in the notebook view. 

Ctrl + Shift + E: The same, but place a different note as a hierarchical parent to the extracted notes. This is a default note.

Every other function unless otherwise specified is only done in the notebook view. 

---
Ctrl + D: Copy the text you have selected, and adds in the current URL you are in. Uses Chromium shortcuts. Formats both "content" and "source" for efficient retrievable pasting of web information. Adds a timestamp. 

---
Ctrl + T: Destructive. Merge two notes. The note below the currently selected one will be consumed and merged. 

---
Ctrl + Shift + C: Copy an entire note, title and contents included.

Ctrl + Shift + X: Destructive. Ditto; delete originating note.

Ctrl + Shift + V: Paste the note.

---
Del: Destructive. Removes note without prompt. Returns you to the note below the previously present. Useful for efficient deletion.

---
Ctrl + Shift + G: Moves backward in the Recent Notes selection. Like a "back" button but where it takes you is unpredictable. Press it enough times and you should get back to where you want to be.  

---
Ctrl + R: This function is done in the note editor. Extract the selection of text. If it starts with a header, this will be made the title of the subsequent note. Adds in a timestamp.

---
\` (backtick key): Add in a timestamp. 

Ctrl + \`: Create three backticks, which is one end of a Markdown blockquote. 

---
Ctrl + M: Create a note with a title as a timestamp. All functions add a timestamp to the top. Immediately moves to the editor once created.

Alt + M: Create a note, but leave you to specify the title. When either the left mouse button or ENTER is pressed, move into the note editor.

Ctrl + Shift + M: Create a note. Doesn't go into the note editor, useful for quickly creating notes for note structure. 

#### FAST REFACTOR FUNCTIONS

The way this behaves is derivative of how it "doesn't change the screen". We can't stop it from moving the screen, but we can return it with the Recent Notes function. We simply select a note, placing an entry in Recent Notes, and return to it when we are finished with the other note. However, returning the screen will fail if we can't select a note in a particular direction. The user may also prefer a direction to move through when continuously refactoring notes. 

This is slightly unreliable. The Recent Notes tab doesn't always place our selected note in the same position, and there is no clear pattern for why it does this. 

When either selection occurs, the refactor display will open, and once either the left mouse button or enter is pressed (implying the user has selected a destination for the note in Mindforger), the "return" function will activate. The return function can be cancelled by pressing Ctrl + G (but no other keybindings do this).

---
Ctrl + G: Refile a note. Return to the note below the previous when finished.

Ctrl + Down Arrow: Ditto.

Alt + G: Refile a note. Return to the note ABOVE the previous when finished. 

Ctrl + Up Arrow: Ditto.

### WINDOW MANAGEMENT FUNCTIONS

USING THESE FUNCTIONS REQUIRES CHANGING THE CONFIGURATION FILE. IF YOU ARE NOT USING THESE, YOU DO NOT HAVE TO CHANGE IT. 

---
Ctrl + 1: Open / minimize first mindforger window.

Ctrl + 2/3/4: Open / minimize second/etc mindforger window.

---
Ctrl + Q: Minimize / maximize all open windows. 

Ctrl + Shift + Q: Open 2 or last "specific" number of MindForger windows. Different numbers of windows result in different winddow layouts. If there are already open windows, close them. 

Ctrl + Shift + 2/3/4: Open 2/3/4 MindForger windows. This affects how they are tiled. The last function used here, if any, determines the number of windows that Ctrl + Shift + Q will open. 

#### CONFIGURATION 

In order to use these functions, set the first line of "mfutils.cfg" to the directory leading to and including your Mindforger executable, as in the file. Otherwise, it will be unable to start Mindforger and affect the windows.

In order to clean up window alignment, adjust the two numbers below. The first determines the compensation for the taskbar (Y axis), the other the X axis scale adjustment. If one is right, tweak the other. It is configured for 1920x1080. 

### MISCELLANEOUS

Ctrl + B/I/U: Create bold/italic/underline. This is a simple rebind for a more Windows control scheme. Bold/italic have an unused attempt at improving mindforger's stock text formatting functions, which is present in underline.

---
Alt + 1: Toggle hoist.

Ctrl + P: Restart script. Will interrupt anything currently running. 

I removed a function that intended to create hierarchical derivatives of other notes. It doesn't work well, but if you're curious, check out "secret_ctrlN.txt". 

### CONFIGURATION AND MODIFICATION

#### Remapping keys
All key definitions look like this:
```
^Y::
  Code
  Code 
  Code
```
The stuff before the two colons defines the keypress to execute the function.  

AutoHotkey's key aliases are:

^: CTRL

+: SHIFT

!: ALT

If multiple are present, it means multiple must be pressed to execute the command.

If a ~ is present before this, it means that the function is set to only execute to keyboard keypresses (as opposed to script keypresses; sometimes necessary to prevent infinite loops). 

### INSTALLATION

First, install the latest AutoHotkey. Then, click on the script to turn it on. This is done every system restart. A "mfutils.cfg", included with "mfutils_r2.ahk", must be included in the same folder for it to run. Place it to your convenience. 

---

## MISCELLANEOUS ADVICE

* Mindforger distinguishes between "in-note" headers and "note division" headers based entirely on whether there is a space before the header (if there is no space, it's a note divider). This is why imports get a header-derived note layout. 
  * The editor will, regardless of whether there is a space in front, make it have one. This means that new notes cannot be created in MindForger's editor. (Without bug exploitation)
  * If you make a custom stencil, you must then always have a space before headers, or otherwise the first header to break this rule will have everything below it appear, but nothing above.
* AltN + R (Refactor) has a search bar. This is very useful for quickly moving information packets around.
* If you place three dashes below a piece of text, without at least a line dividing the two, it will turn into a header, and be recognized in a buggy way as a separate note. This is useful kind of, but it creates more dashes, and a new metadata tag, every single time you reopen the file, leading to unnecessary bloating.
  * To avoid this, NEVER place a line of text directly above a line divider. Otherwise, you'll create some bizarre later-on file divisions.
  * You can use this regex to "fix" bugged note-headers like this into normal ones. But it will reset the time (which occurs regardless because of the constant header-replacing, so not a big deal).
  * FROM: (^[^#].*[^."?!\r\n])\r\n([^\d#•])
  * TO: ##\1 <!-- Metadata: type: Note; created: 2021-02-08 21:29:21; reads: 1; read: 2021-02-08 22:26:55; revision: 1; modified: 2021-02-08 21:29:21; --> \r\n

* Notebooks (.md files) will preserve their original filename when renamed, but the name WITHIN the notebook will change, and that's what MF shows you.
* Bizarrely, exiting and entering a file both count as "reads". Test it yourself.
* The number of reads in a file refers to you entering it, and has no correspondence to notes within it.  
* The "word list" associations only check for like words within the particular MD file; no separators are tolerated. 

I wrote this entire thing and then lost it so I wrote it again. It is 1 am. 

If you would like support using these tools, please file an issue. While I have little interest in using them, I'll help you to a reasonable extent. 
