# RLC-AI ROI Calculator - Project Context for Claude Code

## Project Overview

**Purpose:** Interactive web-based ROI calculator that helps enterprise buyers quantify the cost savings of adopting RLC-AI (Rocky Linux Container for AI) compared to traditional automated deployment approaches.

**Target Audience:** Technical buyers at enterprise organizations with existing infrastructure automation (Terraform, Ansible, Kubernetes) who need defensible financial justification for RLC-AI adoption.

**Tech Stack:** Pure HTML/CSS/JavaScript (no dependencies, no build process, can be hosted on any static web server)

---

## Business Context

### What is RLC-AI?

RLC-AI is a pre-integrated Linux distribution from CIQ that delivers:
- NVIDIA GPU drivers (latest versions)
- CUDA toolkit (12.8)
- DOCA OFED (for InfiniBand)
- PyTorch (2.8.0)
- AI framework optimizations

**Key Value Proposition:** Organizations with automated deployments still face "automation maintenance burden" - 150+ hours annually maintaining infrastructure-as-code, testing driver/CUDA/PyTorch compatibility, and managing version drift. RLC-AI eliminates this complexity tax.

### Critical Buyer Concerns Addressed

This calculator specifically addresses sophisticated technical buyers who challenged our initial "9x faster than manual setup" messaging with:
1. "We don't deploy manually - we use Terraform + Ansible"
2. "Our automated deployments take 5-8 minutes, not 30 minutes"
3. "Where's the independent validation of these claims?"
4. "What's the ROI over our ACTUAL baseline (automation), not a strawman (manual)?"

The updated calculator compares against **automated deployment baselines**, not manual installation.

---

## File Architecture

### Single File Structure

The calculator is intentionally a **single self-contained HTML file** for maximum portability:
- All CSS in `<style>` block
- All JavaScript in `<script>` block
- No external dependencies
- No build process required
- Can be deployed to GitHub Pages, Netlify, Vercel, or any static host

### Key Sections

1. **Header**: Branding and tagline
2. **Input Section (Left Column)**:
   - Infrastructure profile inputs
   - Deployment approach selector (Automated Rocky, RLC+CUDA, RLC-AI)
   - Environment type (Cloud, On-Prem, Hybrid)
   - Advanced options (collapsible)
3. **Results Section (Right Column)**:
   - Total savings
   - Detailed breakdown by category
   - ROI calculation
   - Investment cost
   - Assumptions and transparency section
4. **Footer**: CTA and legal disclaimers

---

## Key Calculation Logic

### Savings Categories

The calculator computes 7 distinct savings categories:

1. **Automation Maintenance Elimination**
   - Annual cost: 152 hours × engineer rate
   - What it represents: Quarterly updates to Terraform/Ansible, testing, remediation

2. **Integration Validation Overhead**
   - Calculation: 7% error rate × deployments × 3 hours × engineer rate
   - What it represents: Time spent debugging driver-CUDA-PyTorch compatibility issues

3. **Infrastructure-as-Code Simplification**
   - Annual value: 40 hours × engineer rate
   - What it represents: Reduced code complexity (480 lines → 25 lines)

4. **Deployment Time Efficiency**
   - Calculation: Time saved (2.8 min) × GPU cost × GPU count × deployments
   - What it represents: GPU idle time during instance warmup (critical for auto-scaling)

5. **Multi-Cloud Image Maintenance** (cloud only)
   - Per cloud: $16,200 annually
   - What it represents: Cost of maintaining separate images across AWS, Azure, GCP

6. **Configuration Drift Prevention**
   - Calculation: Error rate reduction × deployments × 6 hrs × GPU cost × GPUs
   - What it represents: Production downtime avoided

7. **Day-1 Hardware Support** (optional)
   - User-defined strategic value
   - What it represents: Competitive advantage of accessing new GPU architectures 3-6 months earlier

### Deployment Options

Three comparison baselines:

1. **Automated Rocky/Ubuntu**: Current state for most enterprises (baseline)
2. **RLC + CUDA**: Drivers and CUDA pre-installed, user installs PyTorch ($175-250/node)
3. **RLC-AI**: Complete pre-validated stack ($200-300/node)

---

## Critical Design Principles

### 1. Credibility Through Transparency

**Problem Solved:** Initial version made unverifiable claims.

**Solution:**
- Explicit assumptions section comparing against automated baselines
- Conservative error rates (7% vs 20%)
- Realistic deployment times (5-8 min automated baseline, not 30 min manual)
- Acknowledgment of Tech Preview status
- Offer of methodology documentation and customer references

### 2. Addressing Automation Sophistication

**Problem Solved:** Buyers said "we already automated this."

**Solution:**
- Changed messaging from "setup time savings" to "automation complexity elimination"
- Explicit statement: "RLC-AI doesn't replace your automation—it simplifies it"
- Focus on hidden costs: maintenance burden, testing overhead, version coordination

### 3. Multi-Tier Positioning

**Problem Solved:** Not all buyers need full RLC-AI stack.

**Solution:**
- Three deployment options (Automated baseline, RLC+CUDA, RLC-AI)
- RLC+CUDA as budget-conscious option ($50-75/node less)
- Clear value differentiation between tiers

### 4. Cloud-Specific Value

**Problem Solved:** Cloud buyers have different pain points than on-prem.

**Solution:**
- Multi-cloud image maintenance savings ($16K per cloud)
- Auto-scaling efficiency (faster instance warmup)
- Regional consistency value

---

## Technical Implementation Notes

### JavaScript Logic

The `calculate()` function:
1. Reads all input values
2. Applies different calculation logic based on deployment option selected
3. Shows/hides optional savings categories (cloud, hardware) based on inputs
4. Updates all display values dynamically
5. Calculates ROI and payback period

**Event Listeners:** All inputs trigger recalculation on change.

### CSS Architecture

- **Color scheme**: CIQ brand green (#007B5F) as primary
- **Dark theme**: High contrast for readability
- **Responsive**: Grid layout collapses to single column on mobile
- **Tooltips**: Extensive help text available via hover (info icons)

### Tooltip System

Every input and savings category has a tooltip with:
- **Strong tags** for section headers
- **Tooltip-highlight spans** for key numbers
- Detailed explanation of calculation methodology

---

## Deployment Instructions for GitHub

### Repository Setup

```bash
# Create new repository on GitHub
# Name suggestion: rlc-ai-roi-calculator

# Initialize local repo
git init
git add RLC-AI_ROI_Calculator_Updated.html
git commit -m "Initial commit: RLC-AI ROI Calculator addressing enterprise buyer concerns"

# Connect to GitHub
git remote add origin https://github.com/[YOUR-ORG]/rlc-ai-roi-calculator.git
git branch -M main
git push -u origin main
```

### GitHub Pages Deployment

1. Go to repository Settings → Pages
2. Source: Deploy from branch "main"
3. Folder: / (root)
4. Click Save
5. Site will be available at: `https://[YOUR-ORG].github.io/rlc-ai-roi-calculator/RLC-AI_ROI_Calculator_Updated.html`

**Recommended:** Rename file to `index.html` for cleaner URL:
```bash
mv RLC-AI_ROI_Calculator_Updated.html index.html
git add index.html
git commit -m "Rename to index.html for cleaner GitHub Pages URL"
git push
```

Then URL becomes: `https://[YOUR-ORG].github.io/rlc-ai-roi-calculator/`

### Alternative: Custom Domain Setup

If you want calculator.ciq.com:

1. Add CNAME file to repo:
   ```
   calculator.ciq.com
   ```

2. In DNS settings for ciq.com, add CNAME record:
   ```
   calculator.ciq.com → [YOUR-ORG].github.io
   ```

3. In GitHub Pages settings, set custom domain to `calculator.ciq.com`

---

## File Organization Recommendations

### Minimal Structure

```
rlc-ai-roi-calculator/
├── index.html (the calculator)
├── README.md (for GitHub, explains what this is)
├── CHANGELOG.md (track versions)
└── LICENSE (MIT or Apache 2.0)
```

### README.md Content Suggestion

```markdown
# RLC-AI ROI Calculator

Interactive web calculator for enterprise organizations evaluating RLC-AI adoption.

## What This Calculates

Quantifies cost savings from eliminating AI infrastructure automation complexity:
- Automation maintenance burden elimination
- Integration validation overhead reduction
- Infrastructure-as-Code simplification
- Multi-cloud image maintenance elimination

## Target Audience

Technical buyers at organizations with:
- Existing infrastructure automation (Terraform, Ansible, Kubernetes)
- 100+ GPU nodes in production or planned
- Multi-cloud deployments
- Quarterly infrastructure update cycles

## Live Demo

[Insert GitHub Pages URL here]

## Local Development

No build process needed. Just open `index.html` in a browser.

## Assumptions

All calculations based on validated benchmarks comparing RLC-AI against 
automated Rocky Linux deployments (5-8 minute baseline, not 30-minute manual).

See assumptions section in calculator for full methodology.

## Contact

For CIQ Sales inquiries: [sales email]
For technical questions: [support email]
For benchmark methodology: [documentation link]
```

---

## Version Control Strategy

### Semantic Versioning Recommendation

- **v1.0.0**: Initial public release (this version)
- **v1.1.0**: Minor updates (new input fields, adjusted calculations)
- **v2.0.0**: Major redesign or fundamental calculation changes

### Tag Each Release

```bash
git tag -a v1.0.0 -m "Initial release: Enterprise ROI calculator with automated baseline comparison"
git push origin v1.0.0
```

---

## Maintenance and Updates

### When to Update Calculations

1. **New benchmark data** from Damen or customer deployments
2. **Pricing changes** for RLC-AI subscription tiers
3. **Market feedback** showing assumptions don't match reality
4. **Independent validation** that adjusts error rates or time estimates

### What NOT to Change Without Data

- Error rates (currently 7% automated, 2% RLC-AI)
- Deployment time baselines (5-8 min automated, 3-4 min RLC-AI)
- Maintenance hour estimates (152 hours annually)

**CODE2 Principle**: Never fabricate data. All numbers must be defensible.

---

## Integration Points

### Embed Widget Version

For embedding in ciq.com:

```html
<iframe 
  src="https://calculator.ciq.com" 
  width="100%" 
  height="1200px" 
  frameborder="0">
</iframe>
```

### Lead Capture Integration

To add lead capture before showing results:

1. Add email input field in form
2. Gate results display with "Calculate ROI" button
3. Submit to CRM (HubSpot, Salesforce) via API
4. Then show results

**Privacy Note**: Must include privacy policy link if collecting email.

---

## Testing Checklist

Before deploying updates:

- [ ] Test all three deployment options (Automated, RLC+CUDA, RLC-AI)
- [ ] Verify cloud vs on-prem calculations differ appropriately
- [ ] Test multi-cloud selector (1, 2, 3+ clouds)
- [ ] Verify auto-scaling frequency affects calculations
- [ ] Check tooltip display on all major browsers (Chrome, Firefox, Safari, Edge)
- [ ] Mobile responsiveness test (grid should collapse to single column)
- [ ] Validate ROI calculations manually for edge cases
- [ ] Ensure all assumptions section text is accurate

---

## Known Limitations

1. **Static Assumptions**: Calculator uses fixed assumptions. Doesn't dynamically adjust based on organization size or industry.

2. **No Persistent State**: Values reset on page refresh. Could add localStorage for better UX.

3. **No Export Functionality**: No PDF or CSV export of results. Could add print-friendly CSS.

4. **Single Currency**: Only USD. Could add currency selector.

5. **No Comparison View**: Can't see side-by-side comparison of deployment options. Could add comparison table.

---

## Future Enhancement Ideas

### Priority 1 (High Value, Low Effort)

- Add "Email Results" button with basic form
- Print-friendly CSS for PDF generation
- Permalink with encoded parameters (share specific calculations)

### Priority 2 (Medium Value, Medium Effort)

- Side-by-side comparison table (Automated vs RLC+CUDA vs RLC-AI)
- "Save Calculation" to localStorage
- Customer reference quotes in sidebar

### Priority 3 (High Value, High Effort)

- Backend API for lead capture and CRM integration
- Interactive benchmark methodology explainer
- Industry-specific default values (fintech, research, e-commerce)
- Multi-language support

---

## Critical Buyer Feedback Integration

This version specifically addresses concerns from the November 26, 2025 technical buyer feedback:

### ✅ Addressed Issues

1. **Setup time baseline**: Changed from 30-minute manual to 5-8 minute automated
2. **Benchmark credibility**: Added transparency section, offers methodology docs
3. **Error rate realism**: Reduced from 20% to 7% for automated baseline
4. **Comparison fairness**: Explicit "automated Rocky Linux" baseline, not strawman
5. **Cost transparency**: Clear pricing tiers, volume discounts shown
6. **Validation gaps**: Acknowledges Tech Preview status, offers customer references

### Messaging Shifts

**Old**: "9x faster than manual setup"  
**New**: "Eliminate 150+ hours annually maintaining AI infrastructure automation"

**Old**: "20% error rate reduction"  
**New**: "From 7% automated error rate to <2% with pre-validated integration"

**Old**: "Setup time savings"  
**New**: "Automation maintenance burden elimination + integration complexity reduction"

---

## Legal and Compliance Notes

### Disclaimers Required

The footer includes:
- "Estimates based on industry benchmarks and validated performance data"
- "Actual results vary based on your specific environment"
- "Methodology documentation available upon request"

### Claims Requiring Validation

Every numerical claim in assumptions section must be traceable to:
1. Damen's benchmark data (time measurements)
2. Customer conversations (maintenance hour estimates)
3. Industry research (error rates, DevOps practices)

**No fabricated data** per CODE2 values.

---

## Support and Troubleshooting

### Common Issues

**Issue**: ROI shows as negative  
**Solution**: Normal for small deployments (<100 deployments/year). Calculator should show this honestly.

**Issue**: Tooltips not showing on mobile  
**Solution**: Known limitation - hover doesn't work on touch devices. Consider click-to-reveal alternative.

**Issue**: Numbers seem too high/low  
**Solution**: Check inputs match organization's actual deployment frequency and node count.

---

## Contact Information

**Project Owner**: Brian (CIQ Marketing)  
**Technical Validation**: Damen Knight (CIQ Engineering - Benchmark Data)  
**Pricing Strategy**: Hope Lynch (CIQ Product/Marketing)

**For calculator issues**: Create GitHub issue in repository  
**For calculation methodology questions**: Request benchmark documentation from CIQ Sales

---

## Quick Start for Claude Code

To work with this file:

1. **View**: Open `RLC-AI_ROI_Calculator_Updated.html` in browser
2. **Edit**: Modify HTML in any text editor or VS Code
3. **Test**: Refresh browser to see changes (no build step needed)
4. **Deploy**: Push to GitHub, enable Pages, done

**Key files to understand**:
- Lines 1-350: CSS styling
- Lines 351-650: HTML structure and form inputs
- Lines 651-850: HTML results section
- Lines 851-1100: JavaScript calculation logic

**To modify calculations**: Focus on `calculate()` function starting around line 850.

**To modify messaging**: Focus on assumptions sections and tooltip content.

---

*This calculator represents CODE2 values: Customer-Centric (addresses real buyer concerns), Optimistic (shows actual value), Dedicated (detail-oriented accuracy), Efficient (single-file simplicity), Excellent (professional execution).*
