---
layout: page
title: bash_analyzer
description: Bash-based CLI tool for analyzing and auditing CSV and TSV datasets.
img: assets/img/Shell.png
importance: 3
category: Personal
---

A Bash-based command-line tool for analyzing, auditing, and transforming CSV and TSV datasets.

In data operations, technical support, and system administration environments, the need to quickly inspect and understand CSV or TSV files is a common challenge. However, access to specialized analytics tools, graphical interfaces, or full Python/Pandas environments is not always available—particularly on remote servers, restricted workstations, or lightweight development environments.

**bash_analyzer** is a command-line (CLI) application built entirely in Bash that enables users to inspect, audit, search, filter, merge, and export tabular data directly from the terminal. Designed to be lightweight, portable, and practical, it provides a powerful alternative for data exploration without requiring additional software or leaving the shell.

## Key Features

### Interactive and User-Friendly Interface

Built on **whiptail**, bash_analyzer provides a guided, menu-driven experience that simplifies complex data operations, making them accessible even to users with limited command-line experience.

### File Scan Mode

Quickly assess the structure and contents of a dataset by:

* Automatically detecting file delimiters.
* Counting rows and columns.
* Displaying data previews.
* Identifying duplicate records.

This feature provides a fast and reliable first-pass audit of any CSV or TSV file.

### Data Quality Auditing

Evaluate dataset reliability before analysis by detecting:

* Missing values by column.
* Duplicate rows.
* Data type inconsistencies.
* Unwanted whitespace and common data-quality issues.

These checks help ensure that decisions are based on trustworthy data.

### Advanced Search and Filtering

Perform powerful data exploration directly from the terminal:

* Search using regular expressions.
* Extract rows or columns matching specific conditions.
* Sort records with support for numeric-aware ordering.

All without writing a single line of code.

### Dataset Joining

Combine datasets using SQL-style join operations:

* INNER JOIN
* LEFT JOIN
* RIGHT JOIN
* FULL OUTER JOIN

This enables relational-style data integration using plain CSV or TSV files and a shared key.

### Data Cleaning and Export

Prepare data for downstream use by:

* Removing malformed rows.
* Filling missing values.
* Exporting results to:

  * CSV
  * JSON
  * Markdown
  * Ready-to-execute SQL INSERT statements

### Organized Output Management

All generated results are automatically stored in dedicated directories (`output/` and `history/`), ensuring a clean, traceable, and reproducible workflow.

### Cross-Platform Compatibility

bash_analyzer runs without modification on:

* Linux
* Windows Subsystem for Linux (WSL)
* Git Bash for Windows

### Reliability and Software Quality

The project follows modern software engineering practices, including:

* Automated test suite.
* Continuous Integration (GitHub Actions).
* Static analysis with ShellCheck.
* Maintainable and test-driven development workflows.

## Overview

By combining the flexibility of Unix utilities with an intuitive terminal-based interface, **bash_analyzer** provides a practical and efficient solution for auditing, exploring, and transforming tabular datasets directly from the command line. It is particularly useful in environments where lightweight, portable, and dependency-free tools are essential.

  ![App]({{ site.baseurl }}/assets/img/app.png)

You can explore the full source code and detailed instructions on my [![GitHub Repo](https://img.shields.io/badge/GitHub-View%20Repository-red?logo=github)](https://github.com/aalopez76/bash-analyzer).
