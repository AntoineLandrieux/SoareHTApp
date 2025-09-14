
# SoareHTApp

## Overview

>
> This code helps create a basic Windows application using HTA (HTML Application) with custom window settings. It works only on Windows.
>

**Import SoareHTApp**:

```soare
loadimport "script/SHTApp.soare"
```

## Function: WindowConfig(...)

Purpose: Defines the appearance and behavior of your application window.

Parameters include:

**APPLICATIONNAME**: Name of the app.

**BORDER**: Type of window border (`thick`, `thin`, `none`, `dialog`).

**BORDERSTYLE**: Style of the border (`normal`, `raised`, `raised`).

**ICON**: Path to your app icon (optional).

**CAPTION**, **CONTEXTMENU**, **MAXIMIZEBUTTON**, **MINIMIZEBUTTON**, **SCROLL**, **SHOWINTASKBAR**, **SYSMENU**: Use `yes` or `no` to enable or disable these options.

**WINDOWSTATE**: How the window starts (`normal`, `minimize`, `maximize`)

> [!NOTE]
>
> See [Microsoft Documentation [HTA:APPLICATION]](https://learn.microsoft.com/en-us/previous-versions/ms536495(v=vs.85))
>

**Example**:

```soare
loadimport "script/SHTApp.soare"

let config = WindowConfig(
  "SoareApp";   ? Application name
  "thin";       ? Border
  "normal";     ? Border style
  "";           ? Icon
  "yes";        ? Caption
  "yes";        ? Context menu
  "no";         ? Maximize button
  "no";         ? Minimize button
  "no";         ? Scroll
  "yes";        ? Show in taskbar
  "yes";        ? Sysmenu
  "normal"      ? Window state
);
```

## Function: DefaultWindowConfig()

**Purpose**: Gives you a ready-to-use default window configuration with predefined settings.

**Example**:

```soare
loadimport "script/SHTApp.soare"

let config = DefaultWindowConfig();
```

## Function: CreateApp(Name, WindowConfiguration, Width, Height)

**Purpose**: Builds your application’s HTML window

**Example**:

```soare
loadimport "script/SHTApp.soare"

let config = DefaultWindowConfig();
let app = CreateApp("My App"; config; 800; 600);
```

## Helper Functions

`Insert(App, Raw)`: Adds more HTML/code into your app.

`StyleSheet(CSS)`: Adds CSS styles.

`JavaScript(JS)`: Adds JavaScript code.

`HTMLElement(Tag, Attributes, Value)`: Creates an HTML element.

`OpenHTMLElement(Tag, Attributes)`: Starts an HTML element.

`CloseHTMLElement(Tag)`: Closes an HTML tag.

**Example**:

```soare
loadimport "script/SHTApp.soare"

let config = DefaultWindowConfig();
let app = CreateApp("My App"; config; 800; 600);

? CSS

app = Insert(
  app;
  StyleSheet(`
* {
  color: #ffffff;
  font-family: sans-serif;
}

h1 {
  margin: 50px;
  padding: 50px;
  border: 5px solid #ffffff;
}

body {
  background: #281c45;
}

marquee {
  cursor: pointer;
  width: 50%;
}

#clickme {
  background: #000000;
  padding: 20px;
  text-decoration: none;
  font-weight: bolder;
}

#clickme:hover {
  background: #411d64;
}
  `)
);

? <center>

app = Insert(
  app;
  OpenHTMLElement(
    `center`;
    ``;
  )
);

? <h1>Hello World!</h1>

app = Insert(
  app;
  HTMLElement(
    `h1`;
    ``;
    `Hello World!`
  )
);

? <a href="https://github.com/AntoineLandrieux" id="clickme">Click Me !</a>

app = Insert(
  app;
  HTMLElement(
    `a`;
    `href="https://github.com/AntoineLandrieux" id="clickme"`;
    HTMLElement(
      `marquee`;
      ``;
      `Click Me !`
    )
  )
);

? </center>

app = Insert(
  app;
  CloseHTMLElement(
    `center`;
    ``
  )
)

? JavaScript

app = Insert(
  app;
  JavaScript(`
var button = document.getElementById("clickme");

button.onclick = function () {
  alert("Yes !");
};
  `)
);
```

## Function: RunApp(App)

**Purpose**: Runs the application on Windows:

- Creates an .HTA file.
- Opens the app and waits.
- Deletes the file when it’s done

**Example**:

```soare
loadimport "script/SHTApp.soare"

let app = CreateApp("My App"; DefaultWindowConfig(); 400; 300);

? Content
app = Insert(app; "Hello World!");

RunApp(app);
```

## Variable: \_\_SOARE_SoareHTApp_VERSION\_\_

**Purpose**: SoareHTApp version

**Example**:

```soare
loadimport "script/SHTApp.soare"

write("Using SoareHTApp v"; __SOARE_SoareHTApp_VERSION__; '\n');
```
