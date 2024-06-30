# 2024-Feb-18: Android system keyboard
Used Android studio to design a custom android keyboard, following steps from a [video](https://www.youtube.com/watch?v=cHzU8LfGSYA).
Very basic and lack of many essential features. Compiled successfully, but did not run on the device.

# 2024-Feb-23: Keyman Client
keyman is a keyboard software, where users can create their own keyboards.
Designing can only be done on a computer, however the developed keyboard can run on any smartphone or computer which has keyman already installed.

Designed a custom keyboard. Windows side keyboard was easy to develop and has more options like changing the text in the input field.
The Smartphone keyboard only had special keys and there was no way to modify the text being written according to the keypresses.
This was overcome by using combining characters in the unicode standard, but it was still limited. Only windows keyboard is acceptable with this method.

# 2024-May-17: Exploring more options
Smartphone keyboard development is more important than computer keyboard because:
- Physical keyboards are not customizable, one can only change the skin for different keys, which needs to be bought as a separate hardware product.
- Smartphone keyboards are highly customizable and can even change dynamically, that all with just installing just a new keyboard application.
- More people type on smartphones.
Although windows keyboard looks promising using Keyman, but the development of the smartphone keyboard is more important.
### Figma
[Figma](https://www.figma.com/) is a UI/UX development tool used by clients to demonstrate a mock application interface to the coders. A video demonstration od building a keyboard in Figma
can be seeen [here](https://www.youtube.com/watch?v=Syk6YWKtxmg&t=384s&pp=ygUOZmlnbWEga2V5Ym9hcmQ%3D). The keyboard UI and layout can be built to be the best in Figma, but backend is not that great.
The creator of the video claims that he has no way of implimenting the backspace yet! So no hope!
### Flutter
Flutter is good for developing cross platform apps that can run on android, IOS, web, Windows, Mac, etc. The native keyboard cannot be built with flutter, but in-app keyboards are possible.
The idea is to make a dedicated flutter app, that the user can use to write the text using custom keyboard. The text can simply be coped and pasted, just like a notepad.
This can be a good option to at least demonstrate the concept.
### Android system keyboard
Maybe try system keyboard once again?


# 2024-May-19: Android system keyboard - first run
Searched for different android keyboard projects online, trying to find a simple keyboard. Shortlisted the ["simple-keyboard"](https://github.com/rkkr/simple-keyboard/tree/master) based on the most recent and simple designs from a bunch of options.
The idea is to change the code according to our needs. The keyboard was compiled successfully and run on a device. Build process to generate a ".apk" file was also tested.


# 2024-May-25: Android system keyboard - custom keys

### The XML mess
The keyboard layout files are distributed all over in the folder "app\src\main\res\xml". This is because keyboard supports multiple languages and different layouts. The file for default English(UK) with qwerty layout was backtraced to be the "kbd_qwerty.xml". This file reffered to another file "rows_qwerty.xml" for rows definition, which further reffered other files for individual rows.

The files of interest for individual rows are "rowkeys_qwerty1.xml", "rowkeys_qwerty2.xml" and "rowkeys_qwerty3.xml".
These files use string values, which were found in "KeyboardTextsTable.java" in the folder "app\src\main\java\rkr\simplekeyboard\inputmethod\keyboard\internal". (At this point everything was being found using global search shortcut: **ctrl+shift+F** to find the values)
Another file "rowkeys_qwerty0.xml" has only number row, which is displayed only if a separate number row is enabled.
The file "rowkeys_qwerty4.xml" has spacebar, period, enter and other buttons.
The values defined in "KeyboardTextsTable.java" are used directly in these files.
These files control what to show on keys, what to type, long press and more options available after long press.

### Modification
The files "rowkeys_qwerty0.xml", "rowkeys_qwerty1.xml", "rowkeys_qwerty2.xml", "rowkeys_qwerty3.xml" and "rowkeys_qwerty4.xml" are edited. 

For example, here is a code for q,w and e, modified modified to show different cases. Each string **value** can have single or multiple characters/unicodes.
- **keySpec** - value shown on the keys and typed when pressed.
- **keyHintLabel** - value that is shown at the upper right corner of the key.
- **additionalMoreKeys** - value that appears in a popup when longpressed. Releasing long press types this value.
- **moreKeys** - single or multiple values to display in the long press popup. Slide the finger to reach the desired value, then release to type that.
```
<Key
    latin:keySpec="q"
    latin:keyHintLabel="1"
    latin:additionalMoreKeys="1"/>
<Key
    latin:keySpec="w"
    latin:keyHintLabel="2"
    latin:additionalMoreKeys="2"
    latin:moreKeys="3,4,5" />
<Key
    latin:keySpec="e"
    latin:keyHintLabel="3"
    latin:additionalMoreKeys="3"
    latin:moreKeys="\u00DF,\u0161,\u015B," />
```
Another good feature is that caps lock automatically capitalizes all the letters, so no extra definitions are required. At first, this seemed problematic, as the special characters would also change. But turns out the logic only works on english and other derived alphabets. Special handling is required if caps is not as expected.

For example, the small case hard t is ʈ, which turns to Ʈ rather than the desired Ƭ.

# 2024-May-27: Android system keyboard - custom combination logic
Edited the file "InputLogic.java" in the folder "app\src\main\java\rkr\simplekeyboard\inputmethod\latin\inputlogic" and added a function:
```
private int customLogic(final int codePoint)
```
which contains all the custom logic for character combinations.
## Current Bugs/Limitations
If the cursor is placed in between the written text, then modifier still works on the character previous to the cursor, but it then displaces the cursor to another position.

# 2024-May-29: Android system keyboard - apk release for preview
An app as .apk file is released for preview.

Implemented all custom keys. Implemented all "－" key modifier rules. Tippi and bindi not implemented yet. 

# 2024-May-29: Android system keyboard - apk release for preview
Implemented tippi and bindi. Updated github using git GUI for ease.
