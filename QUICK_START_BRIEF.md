# Quick Start Brief for Claude Code

**Goal:** Deploy RLC-AI ROI Calculator to GitHub Pages

---

## What You Have

3 files in `/mnt/user-data/outputs/`:

1. **RLC-AI_ROI_Calculator_Updated.html** - The actual calculator (single self-contained HTML file)
2. **CALCULATOR_PROJECT_CONTEXT.md** - Comprehensive technical documentation
3. **README.md** - GitHub repository documentation

---

## What This Calculator Does

**Quantifies cost savings** for enterprise buyers adopting RLC-AI vs. their current automated deployment approach (Terraform + Ansible).

**Key insight:** Buyers already have automation. RLC-AI doesn't replace it—it simplifies it by eliminating the "automation maintenance burden" (150+ hours annually maintaining infrastructure-as-code).

**Honest positioning:** Compares against 5-8 minute automated baseline, not 30-minute manual strawman.

---

## Immediate Tasks

### Step 1: Test Locally

```bash
# Open the calculator in a browser
open RLC-AI_ROI_Calculator_Updated.html
```

**What to verify:**
- All three deployment options work (Automated, RLC+CUDA, RLC-AI)
- Tooltips display on hover (info icons)
- Mobile responsive (resize browser window)
- ROI calculation updates when inputs change

### Step 2: Initialize Git Repository

```bash
# Rename for cleaner URL
mv RLC-AI_ROI_Calculator_Updated.html index.html

# Initialize repo
git init
git add index.html README.md CALCULATOR_PROJECT_CONTEXT.md
git commit -m "Initial commit: RLC-AI ROI Calculator v1.0.0"
```

### Step 3: Create GitHub Repository

```bash
# Create repo on GitHub (via web UI or gh cli)
# Then connect:
git remote add origin https://github.com/[ORG]/rlc-ai-roi-calculator.git
git branch -M main
git push -u origin main
```

### Step 4: Enable GitHub Pages

1. Go to repository Settings → Pages
2. Source: Deploy from branch "main"
3. Folder: / (root)
4. Click Save
5. Note the URL: `https://[ORG].github.io/rlc-ai-roi-calculator/`

**Done!** Calculator is live.

---

## File Structure

```
rlc-ai-roi-calculator/
├── index.html                      # The calculator (rename from RLC-AI_ROI_Calculator_Updated.html)
├── README.md                       # Public documentation
├── CALCULATOR_PROJECT_CONTEXT.md   # Technical deep-dive
└── LICENSE                         # Add MIT License
```

---

## Key Technical Details

**No build process.** Pure HTML/CSS/JS. Just push and it works.

**Single file.** All CSS and JavaScript embedded in `index.html`.

**No dependencies.** No npm, no webpack, no frameworks.

**Calculation logic:** See `calculate()` function starting around line 850 in index.html.

---

## Common Questions

### "Can I test changes without deploying?"

Yes. Just open `index.html` in a browser. Refresh to see changes. No build step.

### "How do I modify calculations?"

Edit the `calculate()` function in the `<script>` section (~line 850-1100).

Key constants to adjust:
- `AUTOMATION_MAINTENANCE_HOURS = 152`
- `AUTOMATED_ERROR_RATE = 0.07` (7%)
- `RLC_AI_ERROR_RATE = 0.02` (2%)

### "What if I break something?"

Version control! Create a branch before making changes:
```bash
git checkout -b test-changes
# Make changes, test
git commit -m "Testing calculation adjustments"
# If good:
git checkout main
git merge test-changes
```

### "How do I embed this in ciq.com?"

```html
<iframe 
  src="https://calculator.ciq.com" 
  width="100%" 
  height="1200px" 
  frameborder="0">
</iframe>
```

---

## Critical Design Principles

### 1. Honesty Over Hype

- Shows negative ROI for small deployments (intentional)
- Conservative error rates (7% vs industry 15-30%)
- Realistic automated baseline (5-8 min, not 30 min manual)

### 2. Transparency

- Full assumptions section
- Offers methodology documentation
- Acknowledges Tech Preview status

### 3. Buyer-Centric

- Addresses "we already automated this" objection
- Focuses on automation maintenance burden
- Compares against actual baseline, not strawman

---

## Validation Checklist

Before considering this "done":

- [ ] Tested on Chrome, Firefox, Safari
- [ ] Mobile responsive verified
- [ ] All three deployment options calculate correctly
- [ ] Tooltips display properly
- [ ] Assumptions section is accurate
- [ ] README reflects actual GitHub org/repo names
- [ ] GitHub Pages enabled and working
- [ ] URL shared with stakeholders

---

## Next Steps After Deployment

1. **Share with Sales Team** - Get feedback on messaging
2. **A/B Test** - Track which deployment option buyers select
3. **Iterate Based on Feedback** - Update assumptions as more data comes in
4. **Add Lead Capture** - Email input to send results (optional)
5. **Monitor Usage** - Google Analytics or similar (optional)

---

## Support

**Questions about calculations?** See `CALCULATOR_PROJECT_CONTEXT.md` for detailed methodology.

**Technical issues?** Create GitHub issue.

**Need benchmark data?** Contact Damen Knight (CIQ Engineering).

---

**CODE2 Reminder:** Never fabricate data. All numbers must be defensible. When in doubt, be conservative.
