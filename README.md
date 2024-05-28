# BlackWidow-Chess

![GitHub Repo](https://img.shields.io/github/repo-size/ahmedryasser/ChessMSWE?style=flat-square)
![GitHub License](https://img.shields.io/github/license/ahmedryasser/ChessMSWE?style=flat-square)
![image](https://github.com/ahmedryasser/ChessMSWE/assets/56661044/0a11d325-e0ed-4031-ba42-85c03a1d8da4)

BlackWidow-Chess is a fully functional chess game written in Java. It features a graphical user interface implemented using AWT and Swing, allowing two players to play a game of chess against each other on a single machine. The game also provides features like tracking taken pieces and move history. In this Project me and my team tested the codebase using a plethora of testing strategies, highlighted below.

Testing summary document: [Chess_Testing.pdf](https://github.com/ahmedryasser/ChessMSWE/files/15258018/Chess_Testing.pdf)


## Table of Contents
- [Introduction](#introduction)
- [Features](#features)
- [Installation](#installation)
- [Usage](#usage)
- [Testing](#testing)
- [Continuous Integration](#continuous-integration)
- [Static Analysis](#static-analysis)
- [License](#license)

## Introduction

BlackWidow-Chess is a Java-based chess game that supports two players on a single machine. Key features include move tracking, capturing taken pieces, and analysis through different strategies.

GitHub Repository: [ChessMSWE](https://github.com/ahmedryasser/ChessMSWE)

## Features
- Two-player chess game on a single machine
- Graphical user interface using AWT/Swing
- Move tracking and captured pieces display
- Analysis of chess strategies through testing

## Installation

### Prerequisites
- **Java**: Java Development Kit (JDK) 11+
- **IDE**: IntelliJ IDEA (recommended)

### Building the Project
1. Clone the repository:
    ```bash
    git clone https://github.com/ahmedryasser/ChessMSWE.git
    ```
2. Open the project in IntelliJ IDEA.
3. Add the `guava-18.0.jar` file located in the `lib` directory to the module dependencies:
    - Go to **File > Project Structure**.
    - Under **Modules**, click **Dependencies** and add `guava-18.0.jar`.

4. Mark the `src` directory as the **Sources Root**:
    - Right-click on `src` and select **Mark Directory As > Sources Root**.

5. Run `BlackWidow.java` located in `src/com/chess`.

## Usage

1. Start the game by running `BlackWidow.java` in your IDE.
2. Players can use the GUI to move pieces and play chess.

## Testing

The project includes various test cases to ensure the correct functionality of chess mechanics and game strategies.

### Structure of Test Cases

**Test Suite Files**
- `TestKingSafety`: Tests King Tropism
- `TestMiniMax`: Tests the chess engine's move strategy and evaluation
- `TestPawnStructure`: Tests pawn structure penalties
- `TestPGNParser`: Tests `.pgn` file existence and correctness
- `TestPieces`: Tests piece movement
- `TestPlayer`: Tests player movement functionality
- `TestRookStructure`: Tests rook movement (incomplete)
- `TestStaleMate`: Tests stalemate scenarios
- `ChessTestSuite`: Central test utility for running all test files collectively

### Running Tests

**In IntelliJ IDEA:**
1. Navigate to `tests/com/chess/test` folder.
2. Mark the directory as a **Test Source Root**:
    - Right-click on the folder and select **Mark Directory As > Test Source Root**.
3. Build the project:
    - Right-click on the `tests` folder and select **Rebuild '<default>'**.
4. Run individual test classes or `ChessTestSuite` to execute all test cases.

## Continuous Integration

BlackWidow-Chess integrates continuous integration using GitHub Actions. The `ant.yml` workflow file defines a build pipeline for Apache Ant.

### GitHub Actions Pipeline

The `.github/workflows/ant.yml` file contains the CI pipeline configuration:
```yaml
name: Java CI

on:
  push:
    branches: [ "main" ]
  pull_request:
    branches: [ "main" ]

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
    - name: Checkout Code
      uses: actions/checkout@v2

    - name: Set up JDK 11
      uses: actions/setup-java@v2
      with:
        java-version: '11'

    - name: Build with Ant
      run: ant -buildfile build.xml

    - name: Run Tests with Ant
      run: ant test```


