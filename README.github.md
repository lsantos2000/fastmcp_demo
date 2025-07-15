# FastMCP Demo

A production-ready FastMCP (Model Context Protocol) server with modular architecture, advanced calculator, and comprehensive testing.

## 🚀 Features

- **4 Powerful Tools**: Mathematical operations, advanced calculator, text processing
- **25+ Math Functions**: Trigonometric, logarithmic, statistical functions
- **Security-First Design**: Safe expression evaluation with input validation
- **Comprehensive Testing**: 36 test cases with 100% pass rate
- **Modular Architecture**: Clean, extensible codebase
- **Professional Documentation**: Complete setup and usage guides

## 🛠️ Tools Available

| Tool | Description | Example |
|------|-------------|---------|
| `add` | Add two integers | `add(3, 5)` → `8` |
| `multiply` | Multiply two numbers | `multiply(2.5, 4)` → `10.0` |
| `calculate` | Advanced calculator | `calculate("sqrt(64) + sin(pi/2)")` → `9.0` |
| `greet` | Personalized greeting | `greet("Alice")` → `"Hello, Alice! Welcome to FastMCP."` |

## 🧮 Calculator Capabilities

- **Basic Operations**: `+`, `-`, `*`, `/`, `**`, `%`
- **Trigonometric**: `sin`, `cos`, `tan`, `asin`, `acos`, `atan`
- **Logarithmic**: `log`, `log10`, `log2`, `exp`
- **Advanced**: `sqrt`, `abs`, `floor`, `ceil`, `min`, `max`
- **Constants**: `pi`, `e`
- **Complex Expressions**: `(sqrt(25) + 3) * sin(pi/6)`

## 📁 Project Structure

```
fastmcp_demo/
├── demo.py                     # Main server entry point
├── tools/                      # Tools package
│   ├── __init__.py            # Package initialization
│   ├── math_tools.py          # Mathematical operations
│   └── text_tools.py          # Text processing tools
├── tests/                      # Comprehensive test suite (36 tests)
│   ├── __init__.py            # Test package
│   ├── test_math_tools.py     # Math tools tests
│   ├── test_text_tools.py     # Text tools tests
│   ├── test_integration.py    # Integration tests
│   ├── run_tests.py          # Test runner script
│   └── README.md             # Test documentation
├── requirements.txt           # Production dependencies
├── requirements-dev.txt       # Development dependencies
├── pyproject.toml            # Project configuration
└── README.md                 # This file
```

## 🚀 Quick Start

### 1. Installation

```bash
# Clone the repository
git clone https://github.com/yourusername/fastmcp-demo.git
cd fastmcp-demo

# Install dependencies
pip install -r requirements.txt
```

### 2. Run the Server

```bash
# Start the MCP server
python demo.py
```

### 3. Test the Tools

```bash
# Inspect available tools
fastmcp inspect demo.py

# Interactive development mode
fastmcp dev demo.py

# Install for Claude Desktop
fastmcp install demo.py
```

## 🧪 Testing

Run the comprehensive test suite:

```bash
# Run all 36 tests
python tests/run_tests.py

# Run specific test modules
python tests/run_tests.py test_math_tools
python tests/run_tests.py test_text_tools
python tests/run_tests.py test_integration

# Run with unittest
python -m unittest tests.test_math_tools -v
```

## 📝 Usage Examples

### Basic Operations
```python
# Using the tools directly
from tools.math_tools import add, multiply, calculate
from tools.text_tools import greet

print(add(3, 5))                           # → 8
print(multiply(2.5, 4))                    # → 10.0
print(calculate("sqrt(16) + 2"))           # → 6
print(greet("World"))                      # → Hello, World! Welcome to FastMCP.
```

### Advanced Calculator Examples
```python
# Mathematical expressions
calculate("2 + 3 * 4")                     # → 14
calculate("(5 + 3) ** 2")                  # → 64
calculate("sin(pi/2) + cos(0)")            # → 2.0
calculate("log(e) + log10(100)")           # → 3.0
calculate("sqrt(16) + abs(-5)")            # → 9
calculate("max(5, 3, 8) + min(2, 7, 1)")  # → 9
```

### Claude Desktop Integration
After installing with `fastmcp install demo.py`, you can ask Claude:
- "Add 15 and 27"
- "What's the square root of 64?"
- "Calculate sin(pi/2) + cos(0)"
- "Greet John"

## 🔒 Security Features

- **Safe Evaluation**: Sandboxed mathematical expression evaluation
- **Input Validation**: Regex pattern matching for safe characters
- **Error Handling**: Graceful failure for invalid/malicious inputs
- **No System Access**: Blocked dangerous functions like `__import__`, `open`

## 🎯 Key Technical Features

### Modular Architecture
- Clean separation of concerns
- Easy to extend with new tools
- Professional package structure

### Advanced Calculator
- 25+ mathematical functions
- Smart type handling (int vs float results)
- Word-boundary constant replacement
- Comprehensive error handling

### Testing Excellence
- 36 comprehensive test cases
- Unit, integration, and security tests
- Custom test runner with detailed reporting
- CI/CD ready

## 🔧 Development

### Adding New Tools

1. Create your tool function in the appropriate module:
```python
# tools/your_tools.py
def your_function(param: str) -> str:
    """Your tool description."""
    return f"Result: {param}"
```

2. Export it in `tools/__init__.py`:
```python
from .your_tools import your_function
__all__ = ['add', 'multiply', 'calculate', 'greet', 'your_function']
```

3. Register it in `demo.py`:
```python
from tools.your_tools import your_function
mcp.tool()(your_function)
```

4. Add tests in `tests/test_your_tools.py`

### Running Development Dependencies

```bash
# Install development dependencies
pip install -r requirements-dev.txt

# Run tests with coverage
pytest tests/ --cov=tools --cov-report=html
```

## 📊 Test Results

```
Ran 36 tests in 0.863s
OK (skipped=1)

Test Coverage:
- Math tools: 26 tests ✅
- Text tools: 10 tests ✅  
- Integration: 9 tests ✅
- Security validation: ✅
- Error handling: ✅
```

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Make your changes
4. Add tests for new functionality
5. Run the test suite (`python tests/run_tests.py`)
6. Commit your changes (`git commit -m 'Add amazing feature'`)
7. Push to the branch (`git push origin feature/amazing-feature`)
8. Open a Pull Request

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- [FastMCP](https://github.com/jlowin/fastmcp) - The excellent MCP framework
- [Model Context Protocol](https://modelcontextprotocol.io/) - The protocol specification

## 📞 Support

If you have questions or need help:
- 📧 Open an issue on GitHub
- 📖 Check the [documentation](README.md)
- 🧪 Run the test suite to verify your setup

---

**Built with ❤️ using FastMCP and Python**
