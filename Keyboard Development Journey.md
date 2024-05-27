# 2024-Feb-18: Android system keyboard
Used Android studio to design a custom android keyboard. Very basic and lack of many essential features. Compiled successfully, but did not run on the device.

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

# 2024-May-27: Android system keyboard - custom keys
Implemented custom keys.







