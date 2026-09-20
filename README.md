# penn-portfolio

[![CI](https://github.com/mbaradas/penn-portfolio/actions/workflows/ci.yml/badge.svg)](https://github.com/mbaradas/penn-portfolio/actions/workflows/ci.yml)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)

Two small, end-to-end projects built while completing Penn Engineering's Online Professional Learning sequence (Python, Java, statistics, machine learning, deep learning) in preparation for the MAS-CS Online program. I'm a product manager by trade; these are my proof that I can write, test, and reason about the code myself.

> **All data in this repository is synthetic or public. No employer or client data is used anywhere.**

## Projects

| Project | Courses | One line |
|---|---|---|
| [`order-lifecycle-analyzer/`](order-lifecycle-analyzer/) | C1–C4 (Python, data analysis, Java, OOP & data structures) | Ingest synthetic order events, compute fill rates / latency percentiles / cancel-to-fill ratios in pandas, then reimplement the matching core in Java as a class hierarchy with JUnit tests. |
| [`fill-probability-model/`](fill-probability-model/) | C6–C8 (statistics, ML, deep learning) | Will an order fill within *N* seconds? Baseline → feature engineering → logistic regression → small neural net, with a calibration check and a written verdict on whether the deep model earned its complexity. |

Each project has its own README with the problem statement, approach, how to run it, and results.

## Why these two

Order lifecycles are a domain I know from product work, which keeps the focus on the engineering rather than on learning the domain. The first project exercises the programming fundamentals (data wrangling, OOP design, testing); the second exercises the statistical and ML reasoning, including the part I care most about: knowing when *not* to reach for the bigger model.

## Running things

```bash
# from a project folder, in a Python 3.12 virtual environment
pip install -r requirements.txt
pytest
```

Java pieces build with Maven or Gradle; see the project README.

CI runs `pytest` for each project on every push and pull request (`.github/workflows/ci.yml`).

## Layout

```
penn-portfolio/
├── order-lifecycle-analyzer/   Python analytics + Java matching core
├── fill-probability-model/     Classification pipeline + notebooks
├── .github/workflows/ci.yml    GitHub Actions: Python 3.12, pytest per project
└── LICENSE                     MIT
```

## License

MIT — see [LICENSE](LICENSE).
