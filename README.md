# FastMCP Demo

This demo provides a minimal FastMCP server with **4 powerful tools** organized in a modular structure:

## 🛠️ Tools Structure

### Mathematical Operations (`tools/math_tools.py`)
- **`add`**: Adds two integers
- **`multiply`**: Multiplies two floats  
- **`calculate`**: 🧮 **Advanced calculator** for mathematical expressions
  - Supports basic operations: `+`, `-`, `*`, `/`, `**`, `%`
  - Mathematical functions: `sin`, `cos`, `tan`, `log`, `sqrt`, `abs`, `floor`, `ceil`
  - Constants: `pi`, `e`
  - Parentheses for complex expressions
  - Safe evaluation with error handling

### Text Processing (`tools/text_tools.py`)
- **`greet`**: Returns a personalized greeting

### Package Structure (`tools/__init__.py`)
- Package initialization and exports

## Project Structure

```
fastmcp_demo/
├── demo.py              # Main server entry point
├── tools/               # Tools package
│   ├── __init__.py     # Package initialization
│   ├── math_tools.py   # Mathematical operations
│   └── text_tools.py   # Text processing tools
├── tests/               # Comprehensive test suite
│   ├── __init__.py     # Test package
│   ├── test_math_tools.py      # Math tools tests
│   ├── test_text_tools.py      # Text tools tests
│   ├── test_integration.py     # Integration tests
│   ├── run_tests.py    # Test runner script
│   └── README.md       # Test documentation
├── requirements.txt     # Dependencies
├── requirements-dev.txt # Development dependencies
├── pyproject.toml      # Project configuration
└── README.md           # This file
```

## Setup

1. Clone this repo or unzip the archive.
2. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```
3. Start the server:
   ```bash
   python demo.py
   ```
4. In another terminal, install the MCP into your client (e.g., Claude Desktop):
   ```bash
   fastmcp install demo.py
   ```

## How to Test the MCP Server

### Method 1: Direct Testing with FastMCP CLI

You can test the MCP server directly using the FastMCP CLI:

```bash
# Test the add function
fastmcp call demo.py add --a 3 --b 5

# Test the multiply function  
fastmcp call demo.py multiply --a 2.5 --b 4.0

# Test the greet function
fastmcp call demo.py greet --name "Alice"

# Test the calculator function
fastmcp call demo.py calculate --expression "2 + 3 * 4"
fastmcp call demo.py calculate --expression "sqrt(16) + sin(pi/2)"
fastmcp call demo.py calculate --expression "(5 + 3) ** 2"
```

### Method 2: Interactive Testing

Start an interactive session with your MCP server:

```bash
fastmcp dev demo.py
```

This will start an interactive shell where you can call the tools directly.

### Method 3: Integration with Claude Desktop

1. First, install the server:
   ```bash
   fastmcp install demo.py
   ```

2. The server will be available in Claude Desktop. You can then ask Claude to:
   - "Add 3 and 5"
   - "Multiply 2.5 by 4"
   - "Greet Alice"
   - "Calculate 2 + 3 * 4"
   - "What is the square root of 64?"
   - "Calculate sin(pi/2) + cos(0)"

### Method 4: Manual Server Testing

If you want to see the raw MCP protocol:

```bash
# Start the server manually
python demo.py

# The server will start and wait for MCP protocol messages on stdin/stdout
```

## Usage Examples

### Basic Operations
- `add(3, 5)` → returns `8`
- `multiply(2.5, 4)` → returns `10.0`
- `greet("Alice")` → returns `Hello, Alice! Welcome to FastMCP.`

### Calculator Examples
- `calculate("2 + 3 * 4")` → returns `14`
- `calculate("sqrt(16)")` → returns `4.0`
- `calculate("sin(pi/2)")` → returns `1.0`
- `calculate("(5 + 3) ** 2")` → returns `64`
- `calculate("log(e)")` → returns `1.0`
- `calculate("abs(-42)")` → returns `42`
- `calculate("ceil(3.2)")` → returns `4`
- `calculate("max(5, 3, 8)")` → returns `8`

### Advanced Calculator Features
The calculator supports:
- **Trigonometric**: `sin`, `cos`, `tan`, `asin`, `acos`, `atan`
- **Hyperbolic**: `sinh`, `cosh`, `tanh`
- **Logarithmic**: `log`, `log10`, `log2`, `exp`
- **Power & Root**: `sqrt`, `pow`, `**`
- **Rounding**: `round`, `floor`, `ceil`, `abs`
- **Comparison**: `min`, `max`
- **Constants**: `pi` (3.14159...), `e` (2.71828...)
- **Complex expressions**: `(sqrt(25) + 3) * sin(pi/6)`

## Verification

To verify your server is working correctly:

1. **Inspect the server** (shows available tools):
   ```bash
   fastmcp inspect demo.py
   ```
   This creates a `server-info.json` file with details about your tools.

2. **Start development mode** (interactive testing):
   ```bash
   fastmcp dev demo.py
   ```
   This opens the MCP Inspector in your browser for interactive testing.

3. **Install for Claude Desktop**:
   ```bash
   fastmcp install demo.py
   ```
   After installation, you can use the tools directly in Claude Desktop conversations.

## Troubleshooting

### Common Issues
- **"Module not found" error**: Make sure you've installed dependencies with `pip install -r requirements.txt`
- **Calculator errors**: The calculator uses safe evaluation and will return error messages for invalid expressions
- **Port conflicts**: If the server won't start, try killing any existing Python processes

### Testing Calculator Safety
The calculator is designed to be safe and will reject dangerous expressions:
- ✅ `calculate("2 + 3")` → Safe mathematical expression
- ❌ `calculate("__import__('os')")` → Blocked for security
- ❌ `calculate("open('/etc/passwd')")` → Blocked for security

### Performance Notes
- Simple calculations are nearly instantaneous
- Complex expressions with many nested functions may take slightly longer
- The server can handle multiple concurrent requests

## Quick Reference

### 🔢 Available Tools
| Tool | Purpose | Example |
|------|---------|---------|
| `add` | Add two integers | `add(3, 5)` → `8` |
| `multiply` | Multiply two numbers | `multiply(2.5, 4)` → `10.0` |
| `calculate` | Advanced calculator | `calculate("sqrt(64)")` → `8` |
| `greet` | Personalized greeting | `greet("Alice")` → `"Hello, Alice! Welcome to FastMCP."` |

### 🧮 Calculator Functions
| Category | Functions |
|----------|-----------|
| **Basic** | `+`, `-`, `*`, `/`, `**`, `%` |
| **Trig** | `sin`, `cos`, `tan`, `asin`, `acos`, `atan` |
| **Hyperbolic** | `sinh`, `cosh`, `tanh` |
| **Logarithmic** | `log`, `log10`, `log2`, `exp` |
| **Power/Root** | `sqrt`, `pow` |
| **Rounding** | `round`, `floor`, `ceil`, `abs` |
| **Comparison** | `min`, `max` |
| **Constants** | `pi`, `e` |

## 🧪 Testing

This project includes a comprehensive test suite with 36+ test cases:

### Running Tests
```bash
# Run all tests
python tests/run_tests.py

# Run specific test modules
python tests/run_tests.py test_math_tools
python tests/run_tests.py test_text_tools
python tests/run_tests.py test_integration

# Run with unittest directly
python -m unittest tests.test_math_tools -v
```

### Test Coverage
- **Unit Tests**: Individual tool functionality
- **Integration Tests**: Server configuration and tool registration  
- **Security Tests**: Calculator safety validation
- **Edge Cases**: Error handling and type validation

### Test Results
✅ **36 tests passing** with comprehensive coverage of:
- Mathematical operations (20+ test cases)
- Text processing (10+ test cases)
- Integration and configuration (5+ test cases)



