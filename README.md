# automation_scrape_nyka

Challenges Faced and Solutions Implemented During Nykaa Product Scraping
1. Pagination Issues
Challenge: Product pages loaded dynamically, and pagination didn’t follow a consistent pattern, leading to duplicate or missed products.
Solution:

Dynamically updated page URLs using the page_no parameter.

Tracked unique product links using a Python set() to avoid duplicates.

Stopped pagination when repeated product links were detected.

Result: Retrieved unique listings efficiently and prevented infinite loops or redundant data.

2. Unreliable Product Links & Redirections
Challenge: Some products had missing or dynamic links, and a few redirected unexpectedly.
Solution:

Used XPath to extract only valid and complete links.

Wrapped link extraction in try-except blocks to handle redirections or broken links.

Added a delay before loading each product page to allow full rendering.

Result: All valid product pages were accessed, and failures were gracefully handled without script crashes.

3. Inconsistent Prices & Ratings
Challenge: Prices loaded dynamically, and ratings were sometimes missing or inconsistently displayed.
Solution:

Used WebDriverWait to ensure elements were fully loaded.

Assigned default values like “No star rating” when data was missing.

Result: Achieved consistent and accurate extraction of prices and ratings.

4. Unstructured Skin Type Information
Challenge: Skin type suitability wasn’t available in a consistent format across product pages.
Solution:

Created a dictionary of common skin types.

Used keyword matching and regular expressions to identify skin type references in the product descriptions.

Result: Extracted skin type suitability even when not explicitly listed.

5. Ingredient Extraction Variability
Challenge: Ingredient details appeared under various headings and sometimes weren’t available at all.
Solution:

Modified XPath to search for multiple possible headings like “Ingredients”, “Key Ingredients”, or “Composition”.

Extracted the ingredient text from the adjacent element.

Assigned “Not specified” for missing data.

Result: Improved the quality and consistency of ingredient data across products.

6. Pop-Ups and Slow Page Loads
Challenge: Pop-ups (e.g., login prompts, offers) interrupted scraping, and delayed loads caused element errors.
Solution:

Used explicit waits to ensure all elements were loaded.

Detected and closed pop-ups automatically using try-except blocks.

Introduced a short delay between page loads for stability.

Result: Enhanced script reliability and reduced crashes during scraping.

7. Duplicate Products
Challenge: Some products appeared across multiple categories or pages, leading to redundant scraping.
Solution:

Used a set() to store unique product URLs.

Compared current and previous pages to detect pagination loops.

Result: Efficiently avoided duplication and optimized performance.

8. Performance Optimization
Challenge: Initial script execution was slow due to redundant operations and sleep delays.
Solution:

Enabled headless browser mode to reduce rendering time.

Replaced static delays with dynamic waits using WebDriverWait.

Streamlined logic to handle data extraction more efficiently.

Result: Reduced execution time significantly while maintaining accuracy and stability.

Summary
This project involved overcoming real-world scraping challenges with thoughtful automation strategies. Key improvements include better pagination control, accurate data extraction, faster execution, and robust error handling. The process reflects strong problem-solving skills and adaptability in handling dynamic web content using Selenium.
