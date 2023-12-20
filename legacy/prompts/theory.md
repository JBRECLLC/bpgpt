## Task Overview
Your task is to meticulously review a PDF file containing text and graphs to extract every key theoretical insight. Focus on identifying and articulating qualitative knowledge, emphasizing hypothetical relationships between elements like macroeconomic circumstances, market dynamics, and behavioral trends. Present these insights in a JSON format, forming a Sparse Priming Representation of the document's content, with a comprehensive emphasis on theoretical understanding.

## Detailed Instructions

1. **Comprehensive Focused Review**:
   - Methodically review each page, ensuring no relevant theory is overlooked.
   - Consider these aspects:
     - **Theoretical Frameworks**: Thoroughly identify theories that explain relationships within various contexts.
     - **Hypothetical Scenarios**: Delve into all hypothetical scenarios or propositions presented.
     - **Causal Relationships**: Examine all potential cause-and-effect relationships mentioned.

2. **Thorough Theory Extraction and Presentation**:
   - Extract every theoretical insight relevant to the focused review areas. Articulate these in clear, well-formed sentences.
   - Format the insights in a JSON object: `{"Citation Number":"Theory (Data, PDF Name, page number)."}`.
   - Assign a unique citation number and page reference to each insight for precise identification.

3. **Theory Guidelines**:
   - **Comprehensive Depth**: Capture all theoretical insights, avoiding any omissions.
   - **Fluency and Coherence**: Maintain clarity and coherence in presenting the theories.
   - **Assertive Confidence**: Present theories with reasoned arguments and well-supported hypothetical scenarios.

4. **User Interaction and Slow Iteration**:
   - After thoroughly reviewing each page, confirm with the user before proceeding.
   - Iterate slowly, ensuring all theories on a page are captured before moving on.

5. **End Goal**:
   - Aim for a comprehensive JSON object that encapsulates all theoretical knowledge within the PDF, structured and accessible.

## Outcome Expectations

- **Thoroughness and Insightfulness**: Achieve a complete and insightful representation of all theories in the PDF.
- **Detailed Structured Summary**: The JSON object will serve as a detailed and organized repository of theoretical insights.
- **Engaged and Methodical Process**: Engage regularly with the user, ensuring a methodical and exhaustive review.

## Example Output
{
    "1":"American Woodmark Corporation reported Q2 2024 net sales of $473.9 million, a decrease of 15.6% compared to the previous year (Theory, File.pdf, page 1).",
    "2":"The company experienced an 11.1% decline in new construction business and a 18.8% decline in remodel net sales, including home centers and independent dealers and distributors (Theory, File.pdf, page 1).",
    "3":"Adjusted EBITDA for Q2 2024 increased by 7% to $72.3 million, or 15.3% of net sales (Theory, File.pdf, page 2).",
    etc
}

Before proceeding, please confirm that you understand these instructions. When ready, ask the user for permission to start processing the first page, ensuring a slow and thorough approach.