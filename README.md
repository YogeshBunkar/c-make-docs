# CMAKE Reading Material
### *Fundamentals*  
* Setting Up a Project
    + In-source build 
        - Clutters source code
        - hard to clean     
    + Out-of-source build
        - Clean project
        - Mulitple build types possible

* Minimal CMake Project
    + cmake_minimum_required(VERSION 3.15)

    + project(MyApp)
    + add_executable(myapp main.cpp)
* Targets (Core Concept)
    + Executables
    + Libraries
    + Tests
    + Custom commands

    Example 
    ```
    add_library(mathlib math.cpp)
    add_executable(app main.cpp)
    target_link_libraries(app mathlib)

    app -> uses -> mathlib 
    ```

* Variables
    ```
    set(VERSION_MAJOR 1)
    set(VERSION_MINOR 0)
    
    message("Version: ${VERSION_MAJOR}.${VERSION_MINOR}")
    ```
    + Types
        - Normal variables
        - Environment variables
        - Cache variables

        Cache variables are stored for resue.

        `cmake -DMY_OPTION=ON ..`

* Flow Control
    + CMake also has programming logic
    ```
    // if statement
    if(WIN32)
        message("Windows build")
    endif()

    // loops
    foreach(file a.cpp b.cpp c.cpp)
        message(${file})
    endforeach()
    ```     
* Subdirectories
```
project/
    app/
    library/
    tools/


add_subdirectory(app)
add_subdirectory(library)
```
* Functions and Marcros
```
function(print_name name)
    message("Name: ${name}")
endfunction()

print_name("Jack")
```

* Properties
```
set_target_properties(app PROPERTIES CXX_STANDARD 17)
```

* Generator Expressions
```
target_compile_definitions(app PRIVATE $<$<CONFIG:Debug>:DEBUG_MODE>
)
```