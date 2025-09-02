# Task

**1. Scrape the content of GH advisory - reviewed** 

https://github.com/advisories?query=type%3Areviewed
Eg. [**GHSA-45qj-4xq3-3c45**](https://github.com/advisories/GHSA-45qj-4xq3-3c45)

- Report desc
- Source code
- CWE

**2. Then scrape the associated CWE (if exists / otherwise skip)**

Eg.  https://cwe.mitre.org/data/definitions/77.html

**3. find a fix for the vuln in report description and scrape (if exists / otherwise terminate)**

Eg. https://github.com/zcaceres/markdownify-mcp/commit/a31204de058b22a47e1dcc24508993cfe97e5bb3

**4. Assess the fix**

Give an agent the report - the filediff - the cwe def.
Ask the agent to assess the fix. Good fix? Bad fix?

# Notes

Recommend Firecrawl for scraping: https://www.firecrawl.dev/, https://docs.firecrawl.dev/features/scrape. Eg:
```python
# pip install firecrawl-py
from firecrawl import Firecrawl

app = Firecrawl(api_key="fc-YOUR_API_KEY")

# Scrape a website:
app.scrape('firecrawl.dev')
```
Create a free personal API key

Recommend Agno for LLM: https://docs.agno.com/agents/run. Eg:
```python
from typing import Iterator
from agno.agent import Agent, RunResponse
from agno.models.openai import OpenAIChat
from agno.utils.pprint import pprint_run_response

agent = Agent(model=OpenAIChat(id="gpt-4o-mini"))

# Run agent and return the response as a variable
response: RunResponse = agent.run("Tell me a 5 second short story about a robot")

# Print the response in markdown format
pprint_run_response(response, markdown=True)
```
Can provide Anthropic / OpenAI API key upon request.



