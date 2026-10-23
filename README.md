# User Settings Manager

A small Python module for managing user configuration settings stored in a dictionary. It provides functions to add, update, delete, and view settings, with all keys and values normalized to lowercase.

## Features

- **Add** a new setting (rejects duplicates)
- **Update** the value of an existing setting
- **Delete** a setting by key
- **View** all settings in a readable, formatted string
- Case-insensitive keys: `THEME`, `Theme`, and `theme` all refer to the same setting

## Usage

Import the functions (assuming the code is saved as `settings.py`):

```python
from settings import add_setting, update_setting, delete_setting, view_settings

test_settings = {
    'theme': 'dark',
    'notifications': 'enabled',
    'volume': 'high'
}
```

### `add_setting(settings, setting)`

Adds a new key-value pair. The `setting` argument is a `(key, value)` tuple. Both are converted to lowercase.

```python
add_setting(test_settings, ('Language', 'English'))
# "Setting 'language' added with value 'english' successfully!"

add_setting(test_settings, ('THEME', 'light'))
# "Setting 'theme' already exists! Cannot add a new setting with this name."
```

### `update_setting(settings, setting)`

Updates the value of an existing key. The `setting` argument is a `(key, value)` tuple.

```python
update_setting(test_settings, ('THEME', 'Light'))
# "Setting 'theme' updated to 'light' successfully!"

update_setting(test_settings, ('brightness', 'low'))
# "Setting 'brightness' does not exist! Cannot update a non-existing setting."
```

### `delete_setting(settings, key)`

Removes a setting by key (case-insensitive).

```python
delete_setting(test_settings, 'VOLUME')
# "Setting 'volume' deleted successfully!"

delete_setting(test_settings, 'missing')
# "Setting not found!"
```

### `view_settings(settings)`

Returns a formatted string of all settings, with each key capitalized and every line ending in a newline.

```python
print(view_settings({'theme': 'dark', 'notifications': 'enabled', 'volume': 'high'}))
```

Output:

```
Current User Settings:
Theme: dark
Notifications: enabled
Volume: high

```

If the dictionary is empty:

```python
view_settings({})
# "No settings available."
```

## Function Reference

| Function | Parameters | Returns |
|----------|-----------|---------|
| `add_setting` | `settings` (dict), `setting` (tuple of key, value) | Success or "already exists" message |
| `update_setting` | `settings` (dict), `setting` (tuple of key, value) | Success or "does not exist" message |
| `delete_setting` | `settings` (dict), `key` (str) | Success or "Setting not found!" message |
| `view_settings` | `settings` (dict) | Formatted settings string or "No settings available." |
