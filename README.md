
# SoareHTApp

Basic Windows application using HTA with SOARE.

>
> SoareHTApp is distributed under the [WTFPL](LICENSE).
>

---

## Make app with [SOARE](https://github.com/AntoineLandrieux/SOARE/)

```soare
? Hello World! App

loadimport "script/SHTApp.soare"

? Create new App

let App = CreateApp(
    "My App !";             ? Title
    DefaultWindowConfig();  ? Window config
    400;                    ? Width
    300                     ? Height
);

? Insert text

App = Insert(App; "Hello World!");  

? Run App

RunApp(App);
```

## Documentation

See [SoareHTApp Documentation](doc/documentation.md)

## Contributing

The SoareHTApp source code is located in the Git repository at [github.com/AntoineLandrieux/SoareHTApp](https://github.com/AntoineLandrieux/SoareHTApp/).
Contributions are most welcome by forking the repository and sending a pull request.

## Credit

See **[AUTHORS file](AUTHORS)**

**Contributors :**

![contributors](https://contrib.rocks/image?repo=AntoineLandrieux/SoareHTApp)
