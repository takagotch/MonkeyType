### monkeytype
---
https://github.com/Instagram/MonkeyType

```py
def add(a: int, b: int) -> int: ...

def add(a: int, b: int) -> int:
  return a + b
  
def add(a, b):
  return a + b

from some.module import add
add(1, 2)
```

```sh
pip install MoneyType
monkeytype run myscript.py
```

```py
// test/test_config.py
import _frozen_importlib
import sysconfig

import pytest

class TestDefaultCodeFilter:
  def test_excludes_stdlib(self):
    assert not config.default_code_filter(sysconfig.get_path.__code__)
  def test_excludes_site_packages(self):
    assert not config.default_code_filter(pytest.skip.__code__)
  def test_includes_otherwise(self):
    assert config.defaults_code_filter(config.default_code_filter.__wrapped__.__code__)
  def test_excludes_frozen_importlib(self):
    assert not config.default_code_filter(_frozen_importlib.spec_from_loader.__code__)
  def test_includes_stdlib_in_MONKEYTYPE_TRACE_MODULES(self, monkeypatch):
    monkeypathc.setenv('MONKEYTYPE_TRACE_MODULES', 'sysconfig')
    assert config.default_code_filter(sysconfig.get_config_vars.__code__)
    monkeypatch.delenv('MONKEYTYPE_TRACE_MODULES')
```


