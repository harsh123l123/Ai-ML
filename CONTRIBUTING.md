# Contributing to the AI & ML Learning Repository

Thank you for your interest in contributing! We welcome all contributions, whether they are fixing typos, improving code quality, adding new notebooks, or suggesting new topics.

Here are the guidelines to ensure a smooth collaboration process:

## How to Contribute

1. **Fork the Repository**: Create a personal copy of this repository on GitHub.
2. **Clone Locally**: Clone your fork to your local system:
   ```bash
   git clone https://github.com/YOUR-USERNAME/Ai-ML.git
   cd Ai-ML
   ```
3. **Set Up the Environment**: Follow the setup instructions in the [installation guide](setup/installation.md) to set up Python, Conda/Pip, and Jupyter.
4. **Create a Branch**: Create a new branch for your feature or fix:
   ```bash
   git checkout -b feature/your-feature-name
   ```
5. **Make Changes**: 
   - Keep notebooks clean and readable.
   - Run all cells in your notebooks before committing, so output is visible.
   - Keep cell output sizes reasonable (avoid committing giant logs or plots).
6. **Verify and Lint**:
   - Ensure your code does not contain syntax errors.
   - Test any code from scratch to ensure it runs out-of-the-box.
7. **Commit & Push**:
   ```bash
   git add .
   git commit -m "Add: Clear description of your changes"
   git push origin feature/your-feature-name
   ```
8. **Open a Pull Request**: Submit your pull request to our `main` branch.

## Jupyter Notebook Guidelines

To keep the repository clean and educational:
- **Use Markdown Cells**: Explain the intuition and theory behind each step before writing code. Use LaTeX format for mathematical equations (e.g., `\( E = mc^2 \)`).
- **Structure Clear Headings**: Use `#`, `##`, `###` headings logically.
- **Provide Exercises**: If you add an exercise, provide a corresponding section or solution cell.
- **Keep Libraries Updated**: Use packages specified in [requirements.txt](requirements.txt).

## Code of Conduct

Please be respectful and supportive to other learners and contributors in the issues and pull request discussions. We are here to learn together!
