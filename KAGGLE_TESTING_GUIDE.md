# Testing Guide for Kaggle

## Step-by-Step Instructions

### 1. Upload Notebook to Kaggle

**Option A: Upload File**
1. Go to https://www.kaggle.com/code
2. Click **"New Notebook"**
3. Click **"Upload"** tab
4. Select `design_portfolio_reviewer.ipynb`
5. Click **"Create"**

**Option B: Copy Content**
1. Go to https://www.kaggle.com/code
2. Click **"New Notebook"**
3. Copy all cells from the notebook
4. Paste into the new Kaggle notebook

### 2. Set Up Google API Key

1. In your Kaggle notebook, click **"Add-ons"** in the top menu
2. Click **"Secrets"**
3. Click **"Add new secret"**
4. Enter:
   - **Name:** `GOOGLE_API_KEY`
   - **Value:** Your Google Generative AI API key
5. Click **"Create"**

**To get your API key:**
- Go to https://aistudio.google.com/apikey
- Sign in with your Google account
- Click **"Create API Key"**
- Copy the key

### 3. Install Required Packages (if needed)

Kaggle notebooks usually have most packages pre-installed. If you encounter import errors, add this cell at the beginning:

```python
# Install missing packages (uncomment if needed)
# !pip install google-generativeai requests beautifulsoup4
```

### 4. Run the Notebook

1. Click **"Run All"** in the notebook toolbar, OR
2. Run cells sequentially by clicking the play button on each cell

**Expected Output:**
- ✓ Libraries Loaded
- ✓ API Key Configured
- ✓ Tool Functions Defined
- ✓ Function Declarations Created
- ✓ Memory System Initialized
- ✓ Logging System Ready
- ✓ Specialized Agent Classes Created
- ✓ Coordinator Agent Initialized
- ✓ Ready for Portfolio Reviews

### 5. Test with Sample Portfolio

The notebook includes a demo cell with a sample portfolio. It should run automatically when you execute all cells.

**To test manually:**

```python
# Test with sample text
sample_text = """
# My Design Project

## Problem
Users struggled with the checkout process.

## Solution
I redesigned the checkout flow to be simpler.

## Results
Cart abandonment decreased by 30%.
"""

report = review_portfolio(sample_text, input_type="text")
display_review_report(report)
```

### 6. Test with URL (Optional)

```python
# Test with a portfolio URL
portfolio_url = "https://example.com/portfolio"

report = review_portfolio(portfolio_url, input_type="url")
display_review_report(report)
```

**Note:** URL fetching requires `requests` and `beautifulsoup4`. If these aren't available, the agent will show a warning but still work with text input.

### 7. View Statistics

```python
# Get review statistics
get_review_statistics()
```

### 8. Export Results

```python
# Export review report
export_review_report(report, "my_review.json")

# Export logs
coordinator.logger.export_logs("agent_logs.json")
```

## Troubleshooting

### Issue: "API Key Error"
**Solution:**
- Verify the secret name is exactly `GOOGLE_API_KEY` (case-sensitive)
- Check that the API key is valid
- Ensure you've clicked "Create" after adding the secret

### Issue: "Web libraries not available"
**Solution:**
- This is okay! The agent will still work with text input
- URL fetching is optional
- To enable URL fetching, add: `!pip install requests beautifulsoup4`

### Issue: "Coordinator not initialized"
**Solution:**
- Check that the API key was configured correctly
- Re-run the API Configuration cell
- Verify the secret is accessible

### Issue: Import Errors
**Solution:**
- Kaggle should have all required packages
- If missing, add installation cell:
  ```python
  !pip install google-generativeai
  ```

### Issue: Rate Limits
**Solution:**
- Google API has rate limits on free tier
- Wait a few minutes between requests
- Consider upgrading API plan if needed

## Quick Test Checklist

- [ ] Notebook uploaded to Kaggle
- [ ] API key added to Secrets
- [ ] All cells run successfully
- [ ] Coordinator initialized
- [ ] Sample portfolio review works
- [ ] Report displays correctly
- [ ] Statistics function works

## Expected Runtime

- **First run:** ~30-60 seconds (initialization)
- **Each review:** ~20-40 seconds (depends on content length)
- **Total for demo:** ~1-2 minutes

## Tips

1. **Save frequently:** Kaggle auto-saves, but you can also manually save
2. **Check outputs:** Review each cell's output for errors
3. **Start small:** Test with short portfolio text first
4. **Monitor API usage:** Check your Google AI Studio dashboard
5. **Use demo cell:** The included sample portfolio is perfect for testing

## Next Steps

After successful testing:
1. Verify all features work
2. Test with real portfolio URLs/text
3. Export reports and review them
4. Check statistics and analytics
5. Prepare for submission!

---

**Need Help?**
- Check Kaggle Notebooks documentation
- Review Google Generative AI API docs
- Check the README.md for more details

