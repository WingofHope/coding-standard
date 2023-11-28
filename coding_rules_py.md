# Python 编码规范

## Python 版本

所有代码必须和[Python 3.10](https://peps.python.org/pep-0619/)兼容

## 代码风格和规范
所有代码应当遵循[PEP 8 - Style Guide For Python Code](https://pep8.org)

- **代码一行最多长度**: 不超过100 个字符
- **代码自动格式化**: 推荐使用 [Black](https://github.com/psf/black), 推荐版本号为 22.3.0， 使用pip 进行安装 `pip install black`
- **代码风格**: 函数名最好采用小驼峰式命名法（lowerCamelCase），类名采用大驼峰式命名法（UpperCamelCase）， 变量采用下划线命名法 （`abc_def` 形式）
- **代码字段**: 所有代码除了注释需要用美式英语进行拼写，不允许存在拼写错误。代码注释可以使用中文。

推荐使用[Pylint](https://www.pylint.org) 来检查代码质量。 

## 代码文档
所有代码必须用Doc-string 注释和内联注释。 例如:
```python
def calculate_area(radius):
    """
    计算圆的面积。

    参数:
    radius (float): 圆的半径。

    返回:
    float: 圆的面积。
    """

    # 圆面积的计算公式是 π * r²
    area = 3.14159 * radius ** 2

    return area

```

## 代码测试
所有代码需要有测试
1. 使用标准测试框架
 - 选择测试框架：使用标准的测试框架，如unittest（Python标准库中的测试框架），pytest（第三方库，提供更多功能和简洁的语法）。
2. 测试文件和测试用例的命名
 - 测试文件命名：测试文件通常以test_为前缀，例如test_module.py。
 - 测试用例命名：测试方法应该有描述性的名称，如test_function_does_this。
3. 独立性和隔离性
 - 测试用例独立性：每个测试用例应该独立于其他测试，不应该共享状态。
 - 清理操作：使用setUp()和tearDown()方法来准备和清理测试环境。
4. 使用断言
 - 断言：使用断言来验证测试结果是否符合预期。例如，assertEqual()，assertTrue()，assertRaises()等。
5. 测试覆盖率
 - 覆盖率：尽可能提高代码的测试覆盖率。考虑包括边界条件、异常情况和常规操作。
6. 文档和注释
 - 文档：在测试代码中添加必要的文档字符串（docstrings）和注释，说明每个测试的目的和测试逻辑。
7. 避免过度模拟
 - 合理使用Mock：适当使用mock对象来模拟和测试复杂的依赖关系，但避免过度模拟。
8. 组织测试
 - 测试类别：将测试分为不同的类别，如单元测试、集成测试、系统测试等。
 - 使用测试套件：使用测试套件来组织和运行相关的测试用例。

## 代码异常处理
1. 使用try-except块
 - 基本结构：使用try块包裹可能引发异常的代码，然后使用except块来捕获并处理这些异常。
 - 明确异常类型：在except块中尽可能指定具体的异常类型，而不是使用一个通用的except来捕获所有类型的异常。
2. 处理特定异常
 - 针对性处理：对于不同类型的异常应有针对性的处理逻辑。
 - 避免空的except块：不要使用空的except块，这样会隐藏错误而不是处理它们。
3. 生成异常
 - 自定义异常：如果内置的异常类型不足以描述特定错误情况，可以定义自定义异常类。
4. 异常信息
 - 提供有用的错误信息：在引发异常时提供有用的错误信息，以帮助调试。
5. 避免过度使用
 - 不要滥用：只在必要时使用异常处理。不要使用异常处理来控制正常的程序流程


### VSCODE 如何配置
添加以下 `config.json` (Accessible with CTRL + Shift + P "Preferences: Open Settings (JSON)")
```json
{
    "python.formatting.provider": "black",
    "python.formatting.blackArgs": ["--line-length=100"],
    "python.linting.pylintEnabled": true,
    "python.linting.mypyEnabled": true,
    "python.linting.mypyArgs": [
        "--ignore-missing-imports",
        "--follow-imports=silent",
        "--check-untyped-defs"
    ]
}
```

