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
所有代码必须用Doc-string 注释和内联注释。 例如：
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

