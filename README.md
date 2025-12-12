# RLC-AI ROI Calculator

**Interactive web calculator for enterprise organizations evaluating RLC-AI adoption.**

[![Live Demo](https://img.shields.io/badge/demo-live-green)](https://ctrliq.github.io/rlc-ai-roi-calculator/)

---

## What This Calculates

Quantifies measurable cost savings from adopting RLC-AI (Rocky Linux Container for AI) compared to traditional automated deployment approaches:

### Primary Value Categories

1. **Automation Maintenance Elimination** - 150+ hours annually maintaining infrastructure-as-code
2. **Integration Validation Overhead Reduction** - Pre-validated driver/CUDA/PyTorch compatibility
3. **Infrastructure-as-Code Simplification** - Reduce from 480 to 25 lines of deployment code
4. **Deployment Time Efficiency** - Critical for cloud auto-scaling scenarios
5. **Multi-Cloud Image Maintenance** - $16K+ per cloud annually
6. **Configuration Drift Prevention** - Reduce production incidents from compatibility issues
7. **Day-1 New Hardware Support** - 3-6 month advantage on new GPU architectures

---

## Target Audience

Technical buyers and infrastructure leaders at organizations with:

- ✅ Existing infrastructure automation (Terraform, Ansible, Kubernetes)
- ✅ 100+ GPU nodes in production or planned
- ✅ Multi-cloud AI deployments (AWS, Azure, GCP, Oracle)
- ✅ Quarterly infrastructure update cycles
- ✅ Need for defensible ROI justification to CFO/CTO

**Not for:** Organizations still doing manual deployments (different value prop)

---

## Key Differentiators

### Honest Baseline Comparison

This calculator compares against **automated deployment baselines** (5-8 minute provisioning), not strawman manual installation (30 minutes).

### Validated Assumptions

- 7% error rate for automated deployments (vs 2% for RLC-AI)
- 152 hours annual automation maintenance burden
- $16,200 per-cloud image maintenance cost
- Conservative, defensible estimates backed by customer data

### Transparency

- Full methodology disclosure in assumptions section
- Acknowledges Tech Preview status
- Offers benchmark documentation and customer references
- No fabricated data (CODE2 values)

---

## Technology Stack

**Pure HTML/CSS/JavaScript** - No dependencies, no build process.

- Single self-contained HTML file
- No external libraries or frameworks
- Works on any static web host
- No backend required
- Mobile responsive

---

## Quick Start

### View Locally

```bash
git clone https://github.com/ctrliq/rlc-ai-roi-calculator.git
cd rlc-ai-roi-calculator
open index.html  # macOS
# or just open index.html in any browser
```

### Deploy to GitHub Pages

1. Push to GitHub repository
2. Settings → Pages
3. Source: Deploy from branch "main"
4. Folder: / (root)
5. Save

Your calculator will be live at: `https://ctrliq.github.io/rlc-ai-roi-calculator/`

### Embed in Website

```html
<iframe 
  src="https://ctrliq.github.io/rlc-ai-roi-calculator/" 
  width="100%" 
  height="1200px" 
  frameborder="0">
</iframe>
```

---

## File Structure

```
rlc-ai-roi-calculator/
├── index.html                      # The calculator (single file)
├── README.md                       # This file
├── CALCULATOR_PROJECT_CONTEXT.md   # Detailed technical documentation
└── LICENSE                         # MIT License
```

---

## Calculation Methodology

### Deployment Baselines

| Approach | Setup Time | Error Rate | Annual Maintenance |
|----------|-----------|-----------|-------------------|
| **Automated Rocky** | 5-8 min | 7% | 152 hours |
| **RLC + CUDA** | 4.6 min | 5% | ~107 hours |
| **RLC-AI** | 3.7 min | 2% | ~23 hours |

### Example Calculation (500 deployments, 500 nodes)

```
Automation Maintenance:     $22,800  (152 hrs × $150/hr)
Integration Validation:     $15,750  (7% errors × 500 × 3hrs × $150)
IaC Simplification:          $6,000  (40 hrs × $150)
Deployment Efficiency:       $8,900  (GPU idle time savings)
Multi-Cloud Maintenance:    $32,400  (2 clouds × $16,200)
Configuration Drift:        $11,900  (Production downtime avoided)
──────────────────────────────────────
Total Annual Savings:       $97,750

RLC-AI Investment:         -$125,000  (500 nodes × $250)
──────────────────────────────────────
Net Annual Benefit:        -$27,250   ROI: -22%

BUT: Payback in 15 months, positive from Year 2 onward
```

**Note**: Small scale deployments may show negative Year 1 ROI. Calculator shows this honestly.

---

## Assumptions & Data Sources

### Time Measurements

- **Automated Rocky baseline**: 5-8 minutes (industry standard with Terraform + Ansible)
- **RLC-AI deployment**: 3-4 minutes (measured, validated by Damen Knight benchmarks)

### Error Rates

- **Automated deployments**: 7% encounter compatibility issues (conservative vs industry 15-30%)
- **RLC-AI deployments**: <2% (pre-validated integration)

### Maintenance Hours

- **Quarterly automation updates**: 32 hours (driver updates, testing, remediation)
- **Annual automation refactoring**: 40 hours (keeping IaC current)
- **Annual testing overhead**: 40 hours (validation cycles)
- **Failure remediation**: 40 hours (debugging and fixes)
- **Total**: 152 hours annually

### Multi-Cloud Costs

- **Image maintenance per cloud**: $16,200 annually
  - Quarterly updates: 27 hours × 4 = 108 hours
  - 108 hours × $150/hr = $16,200
- **Cross-cloud consistency incidents**: ~1 per month, $1,294 average cost

---

## When Calculator Shows Negative ROI

**This is intentional and honest.**

Small-scale deployments (<200 deployments/year, <200 nodes) may show negative or low ROI in Year 1.

**Why we show this:**
1. **Credibility** - We don't fabricate positive numbers
2. **Long-term value** - Payback typically occurs in 12-18 months
3. **Strategic benefits** - Hard-to-quantify advantages (engineering focus, risk reduction)
4. **Buyer sophistication** - Technical buyers appreciate honesty

**What to do**: 
- Focus on 3-year TCO, not Year 1 ROI
- Emphasize strategic value (new hardware support, engineering time freed)
- Consider if automation maintenance burden is accurately captured

---

## Browser Compatibility

Tested and working on:
- ✅ Chrome/Edge (Chromium) - Latest
- ✅ Firefox - Latest
- ✅ Safari - Latest (macOS/iOS)
- ⚠️ IE11 - Not supported (uses CSS Grid, ES6 JavaScript)

**Mobile**: Fully responsive, single-column layout on screens <968px

**Known Limitation**: Tooltips on mobile require click, not hover (touch device limitation)

---

## Customization Guide

### Modify Pricing Tiers

Edit line ~950 in JavaScript:

```javascript
if (nodes <= 100) {
    pricePerNode = deploymentOption === 'rlc-ai' ? 300 : 250;
    // Adjust these values ^^^
```

### Modify Assumptions

Edit the assumptions in calculate() function:

```javascript
const AUTOMATION_MAINTENANCE_HOURS = 152; // Adjust this
const AUTOMATED_ERROR_RATE = 0.07;        // 7% - adjust this
```

### Add New Savings Category

1. Add HTML breakdown-item div in results section
2. Add calculation in calculate() function
3. Update totalSavings to include new category
4. Add assumption to assumptions section

---

## Contributing

### Reporting Issues

Found a calculation error or display bug? [Create an issue](https://github.com/ctrliq/rlc-ai-roi-calculator/issues)

**Include:**
- Browser and OS version
- Input values used
- Expected vs actual results
- Screenshots if relevant

### Proposing Changes

**Before submitting PR:**
1. Ensure all numbers are backed by data (no fabrication)
2. Test on Chrome, Firefox, Safari
3. Check mobile responsiveness
4. Update assumptions section if calculations change

---

## Data Validation

All claims in this calculator are backed by:

1. **Benchmark measurements** from CIQ Engineering (Damen Knight)
2. **Customer conversations** capturing maintenance hour estimates
3. **Industry research** on automation error rates and DevOps practices

**Methodology documentation available upon request** during enterprise evaluation.

**Customer references available under NDA** for serious prospects.

---

## License

MIT License - See [LICENSE](LICENSE) file for details.

Copyright (c) 2025 CIQ

---

## Contact

**For Sales Inquiries:**  
sales@ciq.com

**For Technical Support:**  
support@ciq.com

**For Calculator Issues:**  
[Create a GitHub issue](https://github.com/ctrliq/rlc-ai-roi-calculator/issues)

**For Benchmark Methodology:**  
Request documentation through your CIQ Sales representative

---

## About RLC-AI

RLC-AI (Rocky Linux Container for AI) is CIQ's pre-integrated Linux distribution delivering:

- ✅ NVIDIA GPU drivers (latest versions)
- ✅ CUDA toolkit (12.8)
- ✅ DOCA OFED (InfiniBand support)
- ✅ PyTorch (2.8.0)
- ✅ AI-optimized kernel and system tuning
- ✅ Validated compatibility across entire stack

**Learn more:** [ciq.com/rlc-ai](https://ciq.com/products/rlc-ai)

**Request Tech Preview Access:** Contact sales@ciq.com

---

## Version History

### v1.0.0 (Current)
- Initial release addressing enterprise buyer feedback
- Automated deployment baseline comparison
- Multi-cloud value calculation
- Transparent assumptions and methodology
- Mobile responsive design

---

*Built with CODE2 values: Customer-Centric • Optimistic • Dedicated • Efficient • Excellent*
