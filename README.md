# C# Projects Collection

A collection of C# .NET 8 projects demonstrating various programming concepts, design patterns, and best practices. This repository serves as a learning resource and reference for common software development patterns in C#.

## Overview

This solution contains 11 projects covering topics such as:
- Algorithm implementation
- API consumption
- Data structures
- Unit testing with mocking
- Performance optimization
- Clean architecture patterns
- File processing

## Projects

### Core Libraries

| Project | Description |
|---------|-------------|
| [FibonacciGenerator](#fibonaccigenerator) | Fibonacci sequence generator with overflow protection |
| [Linked_List](#linked_list) | Generic singly linked list data structure implementation |
| [PasswordGenerator](#passwordgenerator) | Secure password generation utility |
| [NumericTypesSuggester](#numerictypessuggester) | Windows Forms app to suggest appropriate numeric types |

### API & Data Projects

| Project | Description |
|---------|-------------|
| [StarWars_API](#starwars_api) | Star Wars planets statistics analyzer using SWAPI |
| [ChuckNorisJokes](#chucknorisjokes) | Chuck Norris jokes fetcher from public API |
| [CsvDataAccess](#csvdataaccess) | CSV parsing with performance benchmarking |
| [TicketsDataAggregator](#ticketsdataaggregator) | PDF ticket extraction and aggregation |

### Games & Testing

| Project | Description |
|---------|-------------|
| [DiceRollGameToBeTested](#dicerollgametobetested) | Dice guessing game designed for testability |
| [DiceRollGameTests](#dicerollgametests) | Unit tests for the dice game using NUnit and Moq |
| [FibonacciGeneratorTests](#fibonaccigeneratortests) | Unit tests for the Fibonacci generator |

---

## Project Details

### FibonacciGenerator

A library that generates Fibonacci sequences with built-in overflow protection and comprehensive validation.

**Key Features:**
- Generates first `n` Fibonacci numbers (up to 46 to prevent integer overflow)
- Input validation with clear error messages
- Iterative approach for optimal performance

**Usage:**
```csharp
var sequence = Fibonacci.Generate(10);
// Returns: [0, 1, 1, 2, 3, 5, 8, 13, 21, 34]
```

---

### Linked_List

A generic singly linked list implementation that demonstrates fundamental concepts of linked data structures.

**Key Features:**
- Generic type support (`SinglyLinkedList<T>`)
- Implements `ICollection<T>` interface
- Full enumeration support with `yield return`
- Operations: `Add`, `AddToFront`, `AddToEnd`, `Remove`, `Contains`, `Clear`

**Usage:**
```csharp
var list = new SinglyLinkedList<string>();
list.AddToFront("First");
list.Add("Second");
```

---

### PasswordGenerator

A configurable password generation utility with dependency injection support.

**Key Features:**
- Configurable password length (min/max)
- Optional special characters
- Testable design with `IRandom` interface
- Input validation

**Usage:**
```csharp
var generator = new PasswordGenerator(new RandomWrapper());
string password = generator.Generate(8, 16, useSpecialCharacters: true);
```

---

### NumericTypesSuggester

A Windows Forms application that helps developers choose the appropriate numeric type based on value ranges.

**Key Features:**
- Suggests optimal C# numeric type for given min/max values
- Supports integral types: `byte`, `sbyte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `BigInteger`
- Supports floating-point types: `float`, `double`, `decimal`
- Distinguishes between precise and imprecise floating-point needs

---

### StarWars_API

A console application that fetches and analyzes planet data from the Star Wars API (SWAPI).

**Key Features:**
- Consumes the SWAPI REST API
- Displays planet statistics in formatted tables
- Clean architecture with separation of concerns
- Interface-based design for testability

**Architecture:**
- `ApiDataAccess` - HTTP client wrapper
- `DataAccess` - Planet data reading
- `App` - Business logic and statistics analysis
- `UserInteraction` - Console I/O abstraction

---

### ChuckNorisJokes

A console application that fetches random Chuck Norris jokes from a public API.

**Key Features:**
- Async/await pattern for API calls
- Batch joke fetching with parallel HTTP requests
- Category-based joke filtering
- JSON parsing with `System.Text.Json`

**Usage:**
```csharp
var reader = new JokesApiDataReader();
var categories = await reader.ReadAllCategories();
var jokes = await reader.ReadAsync(pages: 1, jokesPerPage: 5, category: "dev");
```

---

### CsvDataAccess

A project demonstrating CSV parsing with performance benchmarking between two implementations.

**Key Features:**
- Two table data implementations for comparison
- Memory usage measurement
- Execution time benchmarking
- Content equality verification

**Implementations:**
- `TableDataBuilder` (Old) - Original implementation
- `FastTableDataBuilder` (New) - Optimized implementation

---

### TicketsDataAggregator

A console application that extracts ticket information from PDF files and aggregates them with culture-aware formatting.

**Key Features:**
- PDF parsing using PdfPig library
- Culture-specific date/time parsing (`.com` ? en-US, `.fr` ? fr-FR, `.jp` ? ja-JP)
- Domain detection from web addresses
- Formatted text output generation

**Architecture:**
- `FileAccess` - Document reading and writing abstractions
- `TicketsAggregation` - Core aggregation logic
- `Extensions` - Web address parsing utilities

---

### DiceRollGameToBeTested

A dice guessing game designed with testability as a primary concern.

**Key Features:**
- 3 attempts to guess the dice roll
- Dependency injection for dice and user communication
- Resource-based message localization
- Clean separation of concerns

**Design:**
- `IDice` - Abstraction for dice rolling
- `IUserCommunication` - Abstraction for user I/O
- `GuessingGame` - Core game logic

---

### DiceRollGameTests

Comprehensive unit tests for the dice game using NUnit and Moq.

**Key Features:**
- Full test coverage of game logic
- Mock-based testing with Moq
- Parameterized tests with `TestCase`
- Setup/Teardown patterns

**Test Coverage:**
- Victory scenarios (first try, third try)
- Loss scenarios (never guesses, guesses on fourth try)
- Message verification
- Interaction counting

---

### FibonacciGeneratorTests

Unit tests for the Fibonacci generator ensuring correctness and edge case handling.

**Test Coverage:**
- Negative input validation
- Overflow prevention (n > 46)
- Empty sequence generation (n = 0)
- Boundary tests
- Sequence correctness verification

---

## Technical Requirements

- **.NET 8.0 SDK**
- **Visual Studio 2022** (recommended)
- **C# 12.0**

## Dependencies

| Package | Used In | Purpose |
|---------|---------|---------|
| NUnit | Test projects | Unit testing framework |
| Moq | DiceRollGameTests | Mocking framework |
| PdfPig | TicketsDataAggregator | PDF text extraction |
| System.Text.Json | API projects | JSON serialization |

## Getting Started

1. **Clone the repository**
   ```bash
   git clone https://github.com/UrosVel97/C-SharpProjects.git
   cd C-SharpProjects
   ```

2. **Open in Visual Studio**
   - Open the solution file in Visual Studio 2022

3. **Restore NuGet packages**
   ```bash
   dotnet restore
   ```

4. **Build the solution**
   ```bash
   dotnet build
   ```

5. **Run tests**
   ```bash
   dotnet test
   ```

## Key Learning Objectives

This repository demonstrates:

- **Algorithm Implementation**: Fibonacci sequence, linked list traversal
- **Design Patterns**: Dependency injection, factory pattern, strategy pattern
- **Testing Practices**: Unit testing, mocking, test-driven development
- **API Consumption**: RESTful API calls, async/await patterns
- **Performance**: Memory optimization, benchmarking, efficient data structures
- **Clean Architecture**: Interface segregation, separation of concerns
- **File I/O**: CSV parsing, PDF extraction, file writing
- **Globalization**: Culture-aware date/time parsing

## License

This project is for educational purposes demonstrating various C# and .NET programming concepts.

## Author

Created by [UrosVel97](https://github.com/UrosVel97)
