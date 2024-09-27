**Function Definition:**

```python
def update_server_config(file_path, key, value):
```

- **`def update_server_config(file_path, key, value):`**: This line defines a function named `update_server_config`. The function takes three parameters:
    - `file_path`: The path to the server configuration file.
    - `key`: The key to be updated in the configuration file.
    - `value`: The new value to be assigned to the specified key.

**Reading the Existing Content:**

```python
with open(file_path, 'r') as file:
    lines = file.readlines()
```

- **`with open(file_path, 'r') as file:`**: This line opens the server configuration file specified by `file_path` in read mode (`'r'`). The `with` statement ensures that the file is automatically closed after the code block within it is executed, even if an exception occurs.
- **`lines = file.readlines()`**: This line reads all the lines from the open file and stores them as a list of strings in the `lines` variable.

**Updating the Configuration Value:**

```python
with open(file_path, 'w') as file:
    for line in lines:
        if key in line:
            file.write(key + "=" + value + "\n")
        else:
            file.write(line)
```

- **`with open(file_path, 'w') as file:`**: This line opens the server configuration file in write mode (`'w'`). If the file already exists, its contents will be overwritten.
- **`for line in lines:`**: This line iterates over each line in the `lines` list.
- **`if key in line:`**: This line checks if the specified `key` is present in the current line.
- **`file.write(key + "=" + value + "\n")`**: If the key is found, this line writes a new line to the file, replacing the old value with the new `value`. The line is constructed as `key=value\n` to maintain the same format as the original configuration file.
- **`file.write(line)`**: If the key is not found, this line writes the original line back to the file without any changes.

**Example Usage:**

```python
server_config_file = 'server.conf'
key_to_update = 'MAX_CONNECTIONS'
new_value = '600'

update_server_config(server_config_file, key_to_update, new_value)
```

- **`server_config_file = 'server.conf'`**: This line sets the path to the server configuration file to `server.conf`.
- **`key_to_update = 'MAX_CONNECTIONS'`**: This line specifies the key to be updated as `MAX_CONNECTIONS`.
- **`new_value = '600'`**: This line sets the new value for `MAX_CONNECTIONS` to `600`.
- **`update_server_config(server_config_file, key_to_update, new_value)`**: This line calls the `update_server_config` function with the specified parameters, updating the `MAX_CONNECTIONS` value in the `server.conf` file to `600`.

This code effectively updates the specified key in the server configuration file, ensuring that the original format and other lines remain unchanged.
