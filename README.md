# Auto Tagging Support Tickets Using LLM

## Objective
Automatically tag customer support tickets into predefined categories using a Large Language Model (LLM). The goal is to leverage zero-shot and few-shot learning techniques to classify free-text tickets and improve tagging accuracy.

## Dataset
- Free-text Support Ticket Dataset (`customer_support_tickets.csv`)  
- Contains ticket metadata such as Ticket ID, Subject, Description, Customer Satisfaction Rating, etc.

## Instructions
1. Use **prompt engineering** or **fine-tuning** with an LLM for classification.
2. Compare **zero-shot** vs **few-shot** performance.
3. Apply **few-shot learning** techniques to improve tag prediction.
4. Output **top 3 most probable tags** per ticket.

## Steps Followed
1. **Load Dataset**: Read the CSV containing ticket text and metadata.
2. **Define Candidate Categories**:  
   `["Login Issue", "Payment Issue", "Bug", "Feature Request", "Other"]`
3. **Zero-Shot Classification**: Predict top-3 tags for each ticket using `joeddav/xlm-roberta-large-xnli`.
4. **Few-Shot Classification**: Use small in-context examples to guide the model and predict top-3 tags.
5. **Save Results**: Store ticket ID, text, top-3 zero-shot/few-shot labels and scores in a CSV (`classified_tickets_results.csv`).
6. **Compare Results**: Analyze agreement between zero-shot and few-shot predictions and average confidence scores.

## Quick Comparison Results
- **Top-1 label agreement**: 17.62% (Zero-Shot vs Few-Shot)  
- **Average top-1 confidence**:  
  - Zero-Shot: 0.810  
  - Few-Shot: 0.889  
- **Observation**: Few-Shot predictions are generally more confident and context-aware.  

### Sample Differences
| Ticket Example |       Zero-Shot |           Few-Shot           |
|----------------|-----------------|------------------------------|
| Product setup issue | Payment Issue (0.94) | Login Issue (0.95) |
| Peripheral compatibility | Other (0.94) | Login Issue (0.96) |
| Network problem | Bug (0.92) | Login Issue (0.74) |
| Account access | Bug (0.53) | Login Issue (0.98) |
| Data loss | Bug (0.90) | Login Issue (0.92) |

## Skills Gained
- Prompt engineering for LLMs  
- LLM-based text classification  
- Zero-shot and few-shot learning  
- Multi-class prediction and ranking  

## Usage
1. Clone this repository.  
2. Install dependencies:
   ```bash
   pip install transformers accelerate datasets pandas
