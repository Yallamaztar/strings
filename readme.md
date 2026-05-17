# GSC String Utility Library (Plutonium T6 - Black Ops II)

## Overview
This library provides a full set of string utilities and formatting helpers for GSC scripting in Plutonium T6 (Black Ops II).

---

## Features
- String manipulation (split, replace, trim, reverse, etc.)
- Formatting system with `sprintf`
- Console and entity printing helpers
- Type detection and validation utilities
- Token-based formatting system
- Lightweight conversion helpers

---

## API Reference
Refer to each functions implementation in the source for detailed behavior

### String Utilities

#### `starts_with(s, prefix)`
Checks if a string begins with a prefix.

#### `ends_with(s, suffix)`
Checks if a string ends with a suffix.

#### `replace(s, from, to)`
Replaces all occurrences of a substring.

#### `split(s, sep)`
Splits a string into an array using a separator.

#### `join(arr, sep)`
Joins an array into a single string.

#### `strip(s)`
Removes leading and trailing spaces.

#### `trim_left(s)`
Removes leading spaces.

#### `trim_right(s)`
Removes trailing spaces.

#### `contains(s, substr)`
Checks if a substring exists inside a string.

#### `reverse(v)`
Reverses a string or array.

#### `char_at(s, index)`
Returns a character at a specific index.

#### `index_of(s, substr)`
Returns the index of a substring.

#### `repeat(s, times)`
Repeats a string multiple times.

#### `count(s, substr)`
Counts occurrences of a substring.

#### `remove(s, substr)`
Removes all occurrences of a substring.

#### `capitalize(s)`
Capitalizes the first letter of a string.

#### `truncate(s, len, suffix)`
Cuts a string to length and adds a suffix.

---

### Formatting / Printing

#### `sprintf(s, ...args)`
Advanced string formatter supporting:
- `%s` string
- `%d` integer
- `%u` unsigned integer
- `%f` float
- `%t` boolean
- `%a` array
- `%c` color

Returns a formatted string.

#### `printf(s, ...args)`
Prints formatted string to console.

#### `printlnf(s, ...args)`
Prints formatted string with newline.

#### `iprintf(s, ...args)`
Prints formatted string to a player entity.

#### `iprintboldf(s, ...args)`
Prints bold formatted string to a player entity.

## Type & Conversion Helpers

#### `len(v)`
Returns array size.

#### `strlen(s)`
Returns string length.

#### `substr(s, start, end)`
Returns substring.

#### `toint(s)`
Converts string to integer safely.

#### `string(v)`
Converts variable to a string.

#### `type(v)`
Returns variable type as string.

#### `tokentype(s)`
Converts format token into readable type.

---

### Validation Helpers

#### `is_valid_token(token)`
Checks if format token is valid.

#### `IsUInt(v)`
Checks if value is unsigned integer.

#### `IsBoolean(v)`
Checks if value is boolean.

#### `IsColor(v)`
Checks if value is a color code.

#### `is_valid_number(v)`
Checks if string is a numeric digit.

#### `is_valid_token(token)`
Validates formatting tokens.

#### `is_whitespace(s)`
Checks if strings contains only whitespaces

---

## Example Usage

```cpp
#include scripts\strings;

#define color_green "^2"

init() {

    s = "hello world";

    if (starts_with(s, "hello")) {
        printlnf("String starts correctly");
    }

    s = replace(s, "world", "universe");
    printlnf("Modified: %s", s);

    parts = split("a;b;c", ";");
    printlnf("First part: %s", parts[0]);

    joined = join(parts, "-");
    printlnf("Joined: %s", joined);

    trimmed = strip("   hello   ");
    printlnf("Trimmed: '%s'", trimmed);

    level thread onPlayerConnect();
}

onPlayerConnect() {
    level endon("game_ended");

    for (;;) {
        level waittill("connected", player);

        printlnf(
            "Player connected: %s %c(guid: %d)",
            player.name,
            "^2",
            player.guid
        );

        player iprintboldf("Welcome, %s!", player.name);
    }
}
```