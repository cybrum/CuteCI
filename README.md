# CuteCI
CuteCI (cute-sy) is a Continous Integration framework for tracking visual changes in Qt5 QWidget applications.

It consists of two main components:
- The library (libcuteci)
- A diff tool (cuteci-diff)

## Library
``libcuteci`` is used to acquire screenshots of your application for later comparison and integrates easily with your codebase.

Integration is as easy as including ``CuteCI.h`` and initializing it (somewhere after the creation of ``QApplication``):


```c++
#include <CuteCI>

// ...

int main(int argc, char** argv) {
  QApplication app(argc, argv);

  QMainWindow win;

  CUTECI_INIT(&win);

  // ...

  return app.exec();
}

```

When CuteCI is not enabled by defining ``CUTECI`` the ``CUTECI_INIT`` instruction will just do nothing, no additional if-guarding required!

When starting your application with CuteCI enabled it will stay in the background and take screenshots of all widgets in your application and then safely close it after a set amount of time.

## Diff Tool
``cuteci-diff`` is used to generate reports based on the information gathered from ``libcuteci``. It can both generate a short summary for the terminal as well as a fancy HTML report! The diff tool is intentionally minimalistic to further help integration with your existing CI solutions.

### Usage
```
cuteci-diff [summary/html] [folderA] [folderB]
```

## Requirements
- A C++14 compatible compiler
  - *Note: Your application does not have to be built in C++14. It's only a requirement for the library itself and the diff tool*
- CMake 3.9 or newer
- Qt 5
## License
CuteCI is licensed under the GNU General Public License v3 or any later version at your option.

See LICENSE.txt for more detailed information.
