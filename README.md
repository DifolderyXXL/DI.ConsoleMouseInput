# Di.ConsoleMouseInput

ConsoleMouseInput it's a library that contains **`WinApi Module`** and **`Console Mouse`** provider.

## Console mouse module

Provides you with **`mouse positions`**:

* Global position.
* Relative to the console window.
* Clamped position relative to the console window.
* Console cursor position (cursor in char buffer).

## WinApi Module

Provides you with **`window api`**:
* Window handle.
* Global cursor position.
* Window rect.
* Client window rect (console content rect).

Provides you with **`console api`**:
* Console window handle.
* Console window information ( offsets, win size, content size ).
* Font used by the console.

# Here is an example of using this lib

> ***Console paint***

```c#
using Di.Common;
using Di.ConsoleMouseInput;

Loop();
while(true)
{   }

static async void Loop()
{
    await Task.Run(() => {
        Vector2<int> pos = new();
        while (true)
        {
            if (!ConsoleWindow.IsMouseInWindowBounds()) // Checking if mouse in console bounds
                continue;

            var newPos = ConsoleWindow.GetConsoleCursorPosition(); // Taking console cursor position
            Console.SetCursorPosition(newPos.x, newPos.y); // Setting cursor to the point
            if (newPos != pos)
            {
                pos = newPos;

                Console.Write('#'); // Drawing the char symbol
            }
        }
    });
}
```

![image](https://github.com/DifolderyXXL/Di.ConsoleMouseInput/assets/87066000/27e14846-682e-488f-bba9-93e21a8445bb)


<sub> Only fantasy limits you. </sub>
