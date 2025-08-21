---
layout: page
title: bash_analyzer
description: Bash-based CLI tool for analyzing and auditing CSV and TSV datasets.
img: assets/img/Shell.png
importance: 1
category: Personal
---

In data operations or technical support environments, the need to quickly analyze CSV or TSV files often arises. However, complex tools or the right graphical interface are not always available. **Bash Data Analyzer** is a command-line interface (CLI) tool built entirely in `Bash` that allows you to inspect, audit, search, and filter large volumes of data directly from a terminal. This makes it a lightweight and powerful solution focused on modernizing the user interface and adding key functionalities to be a robust and practical tool.

Among its features are:

* **Interactive and User-Friendly Menu:** It uses `whiptail` for a guided and uncomplicated user experience, even for those not accustomed to the command line.
* **File Scan Mode:** It inspects your data's structure, detecting delimiters, counting rows and columns, and displaying content previews for a quick audit.
* **Advanced Search and Filtering:** It allows searching with regular expressions, extracting rows or columns under specific conditions, and easily sorting data.
* **Output Management:** The results of the operations are automatically saved in separate folders (`output/` and `history/`), maintaining an organized work environment.

  ![App]({{ site.baseurl }}/assets/img/app.png)

You can explore the full source code and detailed instructions on my GitHub repository:
[bash-analyzer](https://github.com/aalopez76/bash-analyzer)
