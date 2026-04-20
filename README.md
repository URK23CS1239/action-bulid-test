Step 1: app.py
def add(a, b):
    return a + b

def greet(name):
    return f"Hello, {name}!"
📌 Step 2: test_app.py
from app import add, greet

def test_add():
    assert add(2, 3) == 5

def test_greet():
    assert greet("World") == "Hello, World!"
📌 Step 3: requirements.txt
pytest
📌 Step 4: GitHub Actions File

Path:

.github/workflows/test.yml
📌 Easy YAML Code
name: Python CI

on: [push]

jobs:
  test:
    runs-on: ubuntu-latest

    steps:
    - uses: actions/checkout@v3

    - uses: actions/setup-python@v4
      with:
        python-version: 3.11

    - run: pip install -r requirements.txt

    - run: pytest -v
▶️ Step 5: Run Pipeline
git add .
git commit -m "Add tests"
git push origin main
🔍 How to See Output
Go to repo → Actions tab in GitHub
Click workflow

✔ Output:

test_add PASSED
test_greet PASSED
