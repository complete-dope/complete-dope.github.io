---
title : Learning Crawl 4 AI 
date : 2025-02-20
layout : post
---

# Crawl-4-AI 

* Getting relevant data from the whole site
Pass in schema's along with css / xpath classes that you require to get queried ..

```python
import asyncio, json
from crawl4ai import AsyncWebCrawler, CrawlerRunConfig, CacheMode
from crawl4ai.extraction_strategy import JsonCssExtractionStrategy

async def main():
    schema = {
        "name": "Products",
        "baseSelector": "div.product",
        "fields": [
            {"name": "title", "selector": "h2", "type": "text"},
            {"name": "price", "selector": "span.price", "type": "text"}
        ]
    }
    async with AsyncWebCrawler() as crawler:
        result = await crawler.arun(
            url="https://example.com/products",
            config=CrawlerRunConfig(
                extraction_strategy=JsonCssExtractionStrategy(schema),
                cache_mode=CacheMode.BYPASS
            )
        )
        data = json.loads(result.extracted_content)
        print("Extracted data:", data)

asyncio.run(main())
```

* Get the full markdown for the page :

wait_for : <page-load>


* Content Selection (select limited content )
https://docs.crawl4ai.com/core/content-selection/

* 

















