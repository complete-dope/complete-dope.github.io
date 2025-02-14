---
layout : post 
date : 2025-02-10
title : Web Scraping
---

# Learning to scrape web 

The modern web is dynamic, so we need to use a tool that can atleast scrape dynamic content and get the relevant resutls 

The static scraping sites like : Requests , cheerio, they dont work for dynamic site 

Dynamic sites scraping : Use tools like playwright ( inject javascript on site load and get the data ) 

But modern sites catch this data (playwright) 

## We have something called Chrome Devtools Protocol ( CDP )

CDP is a low-level, JSON-based protocol that allows external tools to interact directly with Chromium-based browsers (like Chrome and the Chromium engine used by Edge).

When you launch a Chromium browser with remote debugging enabled, it opens a WebSocket server. Automation tools (like Playwright or Puppeteer) establish a WebSocket connection to this server.
try this with `firefox --remote-desktop-session=9222`

CDP is a connection between your automation tool and browser 

