I am building a detailed report from a list of uncategorized "Data Points". I want to use an LLM based assistant to help me generate this report. The report generation process is extremely complex, and in order to generate the correct output, I will need to provide detailed instructions one step at a time. I need you to help me think of a strategy for prompting the LLM, storing its output into intermediate files that I will maintain, and asking it to move to the next step given the intermediate output.

The detailed report is a survey of real estate phenomena, curated for executives in the real estate industry. The audience will be explained in a "Persona". For now, let's set the audience "Persona" to "Building Products Customers" (are often companies that specialize in home construction, home repair and renovation, or are building products dealers that purchase building products from manufacturers and sell to end customers.). At various stages throughout the prompting process, the LLM will be given additional details and instructions-- for example, what types of questions the report should answer, how to group "Data Points" into categories, instructions to make sure all "Data Points" are considered in the analysis, instructions on particular trends to look for, etc.  These instructions are too complicated to send in one big zero-shot prompt, so we will need to split the prompts into multiple messages (probably about 7 separate messages in the same thread).

The report consists of "Report Sections", which has 3-7 "Insights", which have 3+ supporting "Data Points". An "Insight" is a pattern or trend about the real world based on events in the past, present, or future. "Insights" tell the story of how macroeconomic events influence consumer preferences/options/behaviors, and how consumer preferences/options/behaviors influence demand. The final report will be in the following format:

```
Report Section: <either 'Current Conditions', 'Demand Drivers', or 'Demand Outlook'. These terms will be defined later>
Insight Attention-Grabber: <a 1 short (3-7 word) restatement of an observed phenomenon relating to consumer preferences/options/behaviors, and how that observed phenomenon has/is/will influence demand. This is a short restatement of the "Insight".>
Insight Description: <a 1-2 sentence explanation of the observed phenomenon.>
Insight Explanation: <a 3-5 paragraph exapansion on the "Insight". This expansion explores the narrative "macroeconomic events -> consumer behaviors -> demand trends". The expansion is strictly data driven, and avoids speculation. It relies exclusively on the "Data Points" provided.>
Supporting Evidence: <a list of all the "Citation IDs" that corroborate this "Insight">
```

Each "Report Section" will have 3-7 "Insights". Each "Insight" will have at least three supporting "Data Points". Each "Insight" should represent about a page of full text. Since the output will be so large (about fifteen total pages), we will need to prompt the LLM to iterate through the insights one by one. We will need to be clever about how we call the LLM's attention to its first prompt (which will overview the entire process briefly), its previously generated output, and the detailed instructions it receives with every new message.

---

Here are some examples of the "data points" that I will give the LLM:
```
{
    "1": "Muted growth expected in 2024 after a contraction in 2023, with high interest rates and a cautious consumer segment limiting large housing-related purchases in the first half of 2024 (Data, Burns-Building-Products-AF_Q3 2023_Part2.pdf, page 1).",
    "2": "Increase in spending on smaller remodeling projects, with households reducing project scopes and phasing projects to manage risk. Real income gains and easing inflation support growth in these projects (Data, Burns-Building-Products-AF_Q3 2023_Part2.pdf, page 1).",
    "3": "Potential shortfall in household income growth against sticky inflation as a downside risk (Data, Burns-Building-Products-AF_Q3 2023_Part2.pdf, page 1)."
}
```
In these examples, the key is the "Citation ID", and the value is the "Data Point". At the end of every "Data Point" is the "Citation", or original source of the "Data Point".

---

Here is an example of an "Insight" from the "Demand Drivers" "Report Section":

```
Report Section: Demand Drivers
Insight Attention-Grabber: Households Increasingly Value Outdoor Living
Insight Description: Household preferences have shifted, driven by attitude changes following the pandemic, smaller new construction, and the lock-in affect of rising interest rates.
Insight Explanation:  Following the onset of the COVID-19 pandemic, household preferences have shifted towards an expansion of outdoor living spaces. This shift is driving spending on outdoor living products such as decks and porches. During the pandemic, homeowners spent a large portion of their time at home, a trend that has continued beyond the end of the pandemic. Two-thirds or more of young and family homeowners say that the pandemic has made their outdoor spaces more important to them. 
Higher home prices and smaller square footage per home have also led to an increased valuation of outdoor living. Homeowners are substituting indoor square footage for comfortable outdoor space, leading to an increase in purchases of decks and porches. 30% of urban homeowners would trade indoor space for a larger outdoor space. 
Rising interest rates are creating a lock-in effect where homeowners with low-rate mortgages are unlikely to move. Homeowners staying in the same home for longer encourages more upgrades to existing homes. XX% of decks and porches installed were made to homes within 2 to 4 years of their purchase date, as opposed to XX% in 2019.
Supporting Evidence: Citation IDs 54, 7, 19, 33, and 105.

```

Note how the "Insight" does two things-- it clearly illustrates the macroeconomic cause of consumer behaviors, and it prognosticates demand patterns. Since the "Insight" describes a phenomenon that will influence demand in specific ways, the "Insight" is put in the "Demand Drivers" "Report Section".