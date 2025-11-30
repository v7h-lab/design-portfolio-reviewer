# Design Portfolio Reviewer Agent

**Track:** Agents for Good (Education)  
**Course:** 5-Day AI Agents Intensive with Google  
**Date:** November 2025

## Problem Statement

Designers struggle to create compelling portfolio case studies that effectively demonstrate their skills, process, and impact. Many portfolios lack:
- Clear storytelling structure
- Evidence of systematic design process (double-diamond)
- Documentation of designer influence and decision-making
- Examples of cross-discipline collaboration

Manual portfolio review is time-consuming and subjective. This agent automates comprehensive portfolio evaluation, providing actionable feedback to help designers improve their case studies.

## Solution

A multi-agent AI system that reviews design portfolios and case studies, evaluating key components and providing detailed, actionable feedback. The system uses specialized agents to assess different aspects of a portfolio, then synthesizes findings into a comprehensive report with improvement recommendations.

## Architecture

### Multi-Agent System

The system consists of 6 specialized agents:

1. **Coordinator Agent** - Orchestrates the review process, routes tasks, and synthesizes final reports
2. **Storytelling Agent** - Evaluates narrative structure, clarity, and engagement
3. **Double-Diamond Agent** - Assesses evidence of discover, define, develop, deliver phases
4. **Designer Influence Agent** - Analyzes decision-making, conflict resolution, and leadership evidence
5. **Collaboration Agent** - Evaluates cross-discipline teamwork and stakeholder engagement
6. **Report Generator Agent** - Synthesizes all evaluations into comprehensive report

### Key Concepts Demonstrated

- ✅ **Multi-Agent System**: Coordinator + 5 specialized agents working sequentially
- ✅ **Custom Tools**: 7 specialized tools (URL fetching, content parsing, evaluation functions)
- ✅ **Memory & Sessions**: ConversationMemory and PortfolioReviewMemory for context and history
- ✅ **Observability**: Comprehensive logging, metrics tracking, export capabilities

## Features

### Input Support
- **URL**: Fetch and analyze portfolios from web URLs
- **Text/Markdown**: Direct text input for portfolio content

### Evaluation Dimensions

1. **Storytelling** (0-100)
   - Narrative structure (beginning, middle, end)
   - Problem statement clarity
   - Solution journey documentation
   - Visual storytelling support
   - Emotional engagement

2. **Double-Diamond Process** (0-100)
   - Discover phase evidence (research, user interviews, data)
   - Define phase evidence (problem framing, insights)
   - Develop phase evidence (ideation, prototyping, iteration)
   - Deliver phase evidence (final solution, testing, launch)

3. **Designer Influence** (0-100)
   - Decision-making documentation
   - Conflict resolution examples
   - Leadership moments
   - Design rationale explanations
   - Stakeholder influence

4. **Collaboration** (0-100)
   - Cross-functional team mentions
   - Collaboration methods/tools
   - Stakeholder engagement
   - Feedback incorporation
   - Team dynamics

### Output

Each review provides:
- Overall score (average of all categories)
- Category-specific scores with detailed breakdowns
- Strengths identified
- Weaknesses/gaps identified
- Specific evidence found (or missing)
- Actionable improvement recommendations
- Prioritized improvement plan

## Setup Instructions

### Prerequisites

- Python 3.7+
- Google Generative AI API key
- Kaggle Notebook environment (or local setup with required libraries)

### Installation

1. **Kaggle Notebook Setup:**
   - Open the `design_portfolio_reviewer.ipynb` notebook in Kaggle
   - Add your Google API key to Kaggle Secrets:
     - Go to Add-ons → Secrets
     - Add secret: `GOOGLE_API_KEY` with your API key value

2. **Local Setup (if not using Kaggle):**
   ```bash
   pip install google-generativeai requests beautifulsoup4
   ```

3. **Configure API Key:**
   - Set `GOOGLE_API_KEY` environment variable, or
   - Modify the notebook to load from your preferred secret management system

### Required Libraries

- `google.generativeai` - Google Gemini API
- `requests` - URL fetching (optional, for URL input)
- `beautifulsoup4` - HTML parsing (optional, for URL input)
- `kaggle_secrets` - Kaggle secrets management (Kaggle only)

## Usage

### Basic Usage

```python
# Review portfolio from text
report = review_portfolio("Your portfolio text here...")

# Review portfolio from URL
report = review_portfolio("https://example.com/portfolio", input_type="url")

# Display results
display_review_report(report)

# Export report
export_review_report(report, "my_review.json")
```

### Advanced Usage

```python
# Search review history
search_review_history("keyword")

# Get statistics
get_review_statistics()

# Export logs
coordinator.logger.export_logs("agent_logs.json")
```

## Example Workflow

1. **Input Portfolio**: Provide URL or paste text content
2. **Multi-Agent Review**: System evaluates across 4 dimensions
3. **Report Generation**: Comprehensive report with scores and recommendations
4. **Review Results**: Display formatted report or export to JSON
5. **Track Progress**: View statistics and search review history

## Architecture Diagram

```
User Input (URL/Text)
    ↓
Coordinator Agent
    ↓
┌─────────────────────────────────────┐
│  Sequential Agent Execution         │
├─────────────────────────────────────┤
│  1. Storytelling Agent              │
│  2. Double-Diamond Agent             │
│  3. Designer Influence Agent        │
│  4. Collaboration Agent              │
└─────────────────────────────────────┘
    ↓
Report Generator Agent
    ↓
Comprehensive Review Report
    ↓
Memory Storage & Export
```

## Technical Implementation

### Custom Tools

1. `fetch_url_content(url)` - Fetches and extracts text from web URLs
2. `parse_portfolio_content(content, format_type)` - Parses content into structured format
3. `evaluate_storytelling(content, context)` - Storytelling evaluation
4. `evaluate_double_diamond(content, context)` - Double-diamond process evaluation
5. `evaluate_designer_influence(content, context)` - Designer influence evaluation
6. `evaluate_collaboration(content, context)` - Collaboration evaluation
7. `generate_improvement_plan(evaluations)` - Creates actionable improvement plan

### Memory System

- **ConversationMemory**: Manages conversation history (max 20 messages)
- **PortfolioReviewMemory**: Stores review history (max 50 reviews) with analytics

### Logging & Observability

- Comprehensive logging of all agent operations
- Performance metrics (response times, tool calls, errors)
- Review statistics and analytics
- Export capabilities (JSON logs, review reports)

## Value Proposition

### For Designers
- **Time Savings**: Automated review saves hours of manual evaluation
- **Objective Feedback**: Consistent, comprehensive evaluation criteria
- **Actionable Insights**: Specific recommendations for improvement
- **Learning Tool**: Understand what makes a strong portfolio case study

### For Educators
- **Consistent Grading**: Standardized evaluation criteria
- **Scalable Review**: Review multiple portfolios efficiently
- **Educational Resource**: Help students understand portfolio best practices

### For Recruiters
- **Quick Screening**: Fast initial evaluation of portfolio quality
- **Structured Assessment**: Consistent evaluation across candidates

## Limitations

- Requires Google Generative AI API access
- URL fetching depends on website accessibility and structure
- Evaluation quality depends on content clarity and completeness
- Best results with well-structured portfolio content

## Future Enhancements

- Support for PDF portfolio files
- Visual analysis of portfolio images/screenshots
- Comparison between multiple portfolios
- Custom evaluation criteria configuration
- Integration with portfolio hosting platforms

## License

This project is part of the Kaggle Capstone Project submission for the 5-Day AI Agents Intensive with Google course.

## Contact

For questions or feedback, please refer to the Kaggle competition discussion forum.

---

**Note**: This agent is designed for educational purposes as part of the Kaggle Capstone Project. Ensure you have proper API key management and follow Google's API usage guidelines.

