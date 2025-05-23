# Source Code Similarity Checker

Source Code Similarity Checker is a tool designed to detect similarity between source codes, even when they have been obfuscated using various techniques. It is ideal for programming teachers and students who want to verify the originality of the code.

## Key Features

- **Similarity Detection:** Detects similarity between source codes, even if they contain obfuscation techniques.
- **Advanced Analysis:** Utilizes tokenization, and edit distance to perform the analysis.

## Technologies Used

- **Python:** Main programming language.
- **Tokenization:** Breaks down the source code into tokens for detailed analysis.
- **Edit Distance:** To measure the similarity between different code fragments.

## Installation

1. Clone the repository:
    ```sh
    git clone https://github.com/EdsonEddy/scsc.git
    ```
2. Navigate to the project directory:
    ```sh
    cd scsc
    ```
3. Install the package:
    ```sh
    pip install .
    ```

## Arguments

- `--path`, `-p`: Path to the directory containing the source code files.
- `--files`, `-f`: Specific input files to compare.
- `--recursive`, `-r`: Recursively search through directories.
- `--threshold`, `-t`: Similarity threshold (default: 0.75, range: 0.0 - 1.0).
- `--method`, `-m`: The method to use for similarity detection. Options are `pysimchecker`, `pycode_similar`, `locmoss`, `codesight` and `shingling` (default: pysimchecker).
- `--verbose`, `-v`: Verbose output.
- `--full-comparison`, `-fc`: Compare each file with every other file and output the results to the specified CSV file.


## Usage

Source Code Similarity Checker can be used from the command line. Here are some usage examples:

### Compare Specific Files
```sh
scsc --files file1.py file2.py
```

### Compare Specific Directory
```sh
scsc --path /path/to/directory
```

### Analyze an Entire Directory
```sh
scsc --path /path/to/directory --recursive
```

### Adjust the Similarity Threshold
```sh
scsc --path /path/to/directory --threshold 0.8
```

### Using the `pycode_similar` Method
```sh
scsc --path /path/to/directory --method pycode_similar
```

### Using the `pysimchecker` Method
```sh
scsc --path /path/to/directory --method pysimchecker
```

### Perfomrm Full Comparison and Output to CSV
```
scsc --path /path/to/directory --full-comparison output_file_name
```

## Output Explanation

### Option `-f` (Specific Files)

When using the `-f` option to compare specific files, scsc generates an output that includes the changes needed to transform one file into another, as well as the similarity percentage between the files. The output has the following format:

```sh
scsc --files file1.py file2.py
```

**Output:**
```sh
[DELETE] Code removed from file1.py
---
[ADD] Code added to file2.py
Similarity Percentage: XX.XX%
```

- **[DELETE]:** Shows the code that was removed from the first file `(file1.py)`. This text will be highlighted in red.
- **[ADD]:** Shows the code that was added to the second file `(file2.py)`. This text will be highlighted in green.
- **Similarity Percentage:** Indicates the percentage of similarity between the two files.

### Option `-p` (Specific Files)

When using the `-p` option to analyze an entire directory, scsc groups the files based on their similarity and displays unique files and groups of similar files. The output has the following format:

```sh
scsc --path /path/to/directory
```

**Output:**
```sh
Files that are similar with file1.py
   file2.py with similarity percentage: XX.XX%
   file3.py with similarity percentage: XX.XX%
File that is unique: file4.py
File that is unique: file5.py
```

- **Files that are similar with:** Shows the files that are similar to the main file `(file1.py)`, along with the similarity percentage. This text will be colored in red.
- **File that is unique:** Shows the files that do not have significant similarity with other files in the directory. This text will be colored in green.

## Contributing

Contributions are welcome. Please follow these steps to contribute:

1. Fork the repository.
2. Create a new branch (`git checkout -b feature/new-feature`).
3. Make your changes and commit them (`git commit -am 'Add new feature'`).
4. Push to the branch (`git push origin feature/new-feature`).
5. Open a Pull Request.

## Additional Documentation
For more information on the techniques used, you can refer to the following resources:

- [Tokenization](https://en.wikipedia.org/wiki/Tokenization)

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for more details.

## Links

- [Repository](https://github.com/EdsonEddy/scsc)
- [Documentation](https://github.com/EdsonEddy/scsc/wiki)
- [Report a Bug](https://github.com/EdsonEddy/scsc/issues)

## Third-Party Licenses

This project includes `locmoss.py` (BSD 3-Clause License) and `pycode_similar.py` (MIT License). Full licenses are at the top of each file. Additionally, `codesight.py` does not have a license in its repository.