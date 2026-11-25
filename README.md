# News Scraper with Python and XPath

An early Python project that fetches news pages, extracts article titles, summaries, and body paragraphs with XPath, and writes one UTF-8 text file per article in a date-stamped folder.

## Try XPath offline

Install the dependencies with `python -m pip install requests lxml`. Save this example as `demo.py` next to [scraper.py](scraper.py), then run `python demo.py`. The example uses fictional HTML and the original scraper’s selectors without contacting the news site.

```python
from lxml import html
from scraper import XPATH_TITLE, XPATH_SUMMARY, XPATH_BODY

article = html.fromstring("""
<article>
  <div class="mb-auto"><text-fill><a>A new neighborhood library</a></text-fill></div>
  <div class="lead"><p>The library opens on Saturday.</p></div>
  <div class="html-content"><p>Visitors can sign up for a free library card.</p></div>
</article>
""")
for selector in (XPATH_TITLE, XPATH_SUMMARY, XPATH_BODY):
    print("\n".join(article.xpath(selector)))
```

Expected output:

```text
A new neighborhood library
The library opens on Saturday.
Visitors can sign up for a free library card.
```

## Original scraper

Run `python scraper.py` from the repository root to attempt the original La República workflow. It relies on the site’s historical HTML structure. If the live site’s markup changes, the selectors may need updating. See [xpath.txt](xpath.txt) for the original selector notes.

[MIT license](LICENSE)
