# Contributing Guidelines

## Adding a New Competition

### Step 1: Create Competition Folder

1. Copy the template from `.template/competition-name-template/`
2. Rename it with the competition name (use lowercase with hyphens)
3. Place it in the `competitions/` directory

```bash
cp -r .template/competition-name-template competitions/your-competition-name
```

### Step 2: Update Competition README

Update the `README.md` in your competition folder with:
- Competition link and details
- Problem description
- Your approach and methodology
- Results and key learnings

### Step 3: Organize Your Notebooks

- Use descriptive names with numbering (e.g., `01-exploration.ipynb`, `02-baseline.ipynb`)
- Keep notebooks focused on specific tasks
- Add markdown cells to explain your thought process
- Include visualizations where appropriate

### Step 4: Update Main README

Add your competition to the "Competitions" section in the main README.md:

```markdown
## Competitions

- **[Competition Name](competitions/competition-folder)** - Brief description
  - Metric: [Score]
  - Ranking: [Position]
```

## Folder Organization

### Directory Structure per Competition

```
competitions/your-competition-name/
├── notebooks/              # Jupyter notebooks
│   ├── 01-exploration.ipynb
│   ├── 02-baseline.ipynb
│   ├── 03-feature-engineering.ipynb
│   └── 04-final-model.ipynb
├── data/                   # Data files (gitignored)
│   ├── train.csv
│   ├── test.csv
│   └── sample_submission.csv
├── models/                 # Saved models (gitignored)
│   ├── baseline_model.pkl
│   └── final_model.pkl
├── src/                    # Python scripts (optional)
│   ├── preprocessing.py
│   └── utils.py
└── README.md              # Competition documentation
```

## Best Practices

### Notebook Organization

1. **Start with data exploration**: Understand the data before modeling
2. **Create a baseline**: Start simple, then iterate
3. **Document everything**: Explain your reasoning and decisions
4. **Track experiments**: Note what works and what doesn't
5. **Clean up before committing**: Remove unnecessary cells and outputs

### Code Quality

- Follow PEP 8 style guidelines for Python code
- Use meaningful variable names
- Add comments for complex logic
- Keep functions small and focused

### Version Control

- Commit frequently with descriptive messages
- Don't commit large data files or model files
- Use `.gitignore` to exclude data and models
- Clear notebook outputs before committing (optional but recommended)

### Documentation

- Update the competition README as you progress
- Document your results and learnings
- Include performance metrics and comparisons
- Note any interesting insights or techniques

## Getting Help

If you have questions or suggestions, feel free to:
- Open an issue
- Submit a pull request with improvements
- Reach out to the repository owner

## Code of Conduct

- Be respectful and constructive
- Share knowledge and learnings
- Give credit where credit is due
- Follow Kaggle's competition rules and ethics
