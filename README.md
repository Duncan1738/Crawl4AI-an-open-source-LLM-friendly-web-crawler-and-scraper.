# 🌐 Crawl4AI: LLM-Friendly Web Crawler & Scraper

Crawl4AI is an open-source, lightweight web crawler and content scraper designed specifically for language model (LLM) applications. It helps extract clean, structured text from web pages and highlight relevant AI/ML concepts such as "transformer", "chatbot", or "machine learning".

---

## 🚀 Features

- ✅ Extracts clean text from any public web page
- 🧠 Detects keywords useful for LLM training or fine-tuning
- 🧹 Removes JavaScript, CSS, and HTML noise
- 🌍 Friendly to modern web pages with dynamic content
- 📦 Simple to use and extend for multi-page crawling

---

## 📦 Installation

```bash
pip install requests beautifulsoup4 fake-useragent

🧪 Usage

from bs4 import BeautifulSoup
from fake_useragent import UserAgent
import requests, re

def crawl_and_extract(url, keywords=None):
    ua = UserAgent()
    headers = {'User-Agent': ua.random}
    response = requests.get(url, headers=headers, timeout=10)
    soup = BeautifulSoup(response.content, 'html.parser')
    for tag in soup(['script', 'style']):
        tag.decompose()
    text = re.sub(r'\s+', ' ', soup.get_text()).strip()
    if keywords:
        found = {kw: kw in text.lower() for kw in keywords}
        return text, found
    return text, None


🔍 Example
url = "https://en.wikipedia.org/wiki/Artificial_intelligence"
keywords = ["machine learning", "transformer", "chatbot"]
text, found = crawl_and_extract(url, keywords)

print("Found Keywords:", found)
print("Preview:", text[:1000])

📊 Output

A cleaned version of webpage text

Boolean indicators of keyword presence

Optional preview display for human inspection

📁 Use Cases

Building LLM training datasets

Scraping public knowledge for AI assistants

Data collection for fine-tuning transformers

Search engine and content indexing

📝 License
MIT License © 2025 Duncan Kibet
