<div align="center">

<picture>
  <source media="(prefers-color-scheme: light)" srcset="/docs/icononly_nobuffer.png">
  <img alt="AlgoMol logo" src="/docs/icononly_transparent_nobuffer.png" width="40%" height="40%">
</picture>

# <p align="center">***AlgoMol***</p>
Calculate Equivalence Classes of Atoms from Molecular Graphs.
</div>

# AlgoMol CLI Tutorial

The AlgoMol CLI provides both an interactive shell mode and a single-shot command mode for analyzing molecular structures.

## Installation

Download from the latest release: [algomol-cli v0.0.1](https://github.com/AlgoMol-dev/AlgoMol-release/releases/tag/v0.0.1)

## Usage Modes

### Interactive Shell Mode

Launch the interactive shell by running the program without arguments:

```bash
./algomol-cli
```

You'll see:
```
AlgoMol CLI v0.0.1
Type 'help' for commands
> 
```

### Single-Shot Mode

Run specific commands directly from your terminal:

```bash
./algomol-cli <command> [options]
```

## Available Commands

### 1. Read SMILES Format

Read a molecule from a SMILES string:

```bash
# From command line
./algomol-cli read-smiles "CC(=O)O" -n "acetic_acid"

# From file
./algomol-cli read-smiles -f molecule.smi -n "my_molecule"
```

Options:
- `-n, --name`: Set molecule name
- `-f, --file`: Read SMILES from file
- `-a, --analyze`: Perform detailed analysis
- `-o`: Write results to `<molecule_name>.txt`
- `--output <path>`: Write results to specified file
- `-d, --draw`: Generate molecule visualization
- `-s, --swap <center> <atom1> <atom2>`: Swap orientations

### 2. Read MOL Format

Read a molecule from a MOL file:

```bash
./algomol-cli read-mol molecule.mol -a -o results.txt
```

Options:
- `-a, --analyze`: Perform detailed analysis
- `-o, --output`: Write results to specified file
- `-d, --draw`: Generate molecule visualization
- `-s, --swap <center> <atom1> <atom2>`: Swap orientations

## Analysis Output

When using the `-a` flag, the analysis includes:
- Basic molecular information (name, atom count, bond count)
- Equivalence classes of atoms
- Other molecular properties

Example output:
```
Molecule Analysis
Name: acetic_acid
Atoms: 8
Bonds: 7

Equivalence Classes:
0
1
2
3
4 5 6
7
```

## Visualization

When using the `-d` flag, the program generates a PNG image of the molecule. The file is named `<molecule_name>.png` by default.

## Tips

1. Use the `-a` flag for detailed analysis when needed
2. The `-o` flag automatically names output files based on molecule name
3. For complex molecules, reading from files is recommended over command-line SMILES
4. Use orientation swapping to adjust molecular geometry as needed

## Examples

1. Basic SMILES reading:
```bash
./algomol-cli read-smiles "CC(=O)O" -n "acetic_acid"
```

2. Full analysis with visualization:
```bash
./algomol-cli read-smiles "CC(=O)O" -n "acetic_acid" -a -d -o
```

3. Reading from MOL file with orientation swap:
```bash
./algomol-cli read-mol molecule.mol -s 1 2 3 -a -d
```

## Error Handling

- Invalid SMILES strings will produce an error message
- File read/write errors will be reported with specific messages
- Invalid atom IDs for orientation swapping will be caught and reported

## Version Information

Check the version:
```bash
./algomol-cli --version
```

## Getting Help

For command-specific help:
```bash
./algomol-cli read-smiles --help
./algomol-cli read-mol --help
```
