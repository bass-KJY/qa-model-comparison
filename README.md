# MRC Model Performance Comparison: Table-based vs Context-based QA

This project compares the performance of a **Machine Reading Comprehension (MRC)** model on two types of data: **table-based QA** and **context-based QA**. The study aims to identify how different data formats impact model performance and uncover the strengths and limitations of the model depending on the data type.

## Project Overview

- **Objective**: Analyze how an MRC model performs differently on table-based vs context-based question answering tasks  
- **Model Used**: [`koelectra-base-discriminator-finetuned-squad_kor_v1`](https://huggingface.co/arogyaGurkha/koelectra-base-discriminator-finetuned-squad_kor_v1)  
- **Datasets**:  
  - [AIHub Table-based QA Dataset](https://aihub.or.kr/aihubdata/data/view.do?dataSetSn=71565)  
  - [AIHub Context-based QA Dataset](https://aihub.or.kr/aihubdata/data/view.do?dataSetSn=106)  
- **Preprocessing**: Unified structure with the keys `Document Title`, `Context`, `Question`, and `Answer`

## Experimental Setup

| Item            | Table-based QA         |   Context-based QA        |
|-----------------|------------------------|---------------------------|
| Data Type       | Structured table data  | Natural language text     |
| Preprocessing   | array → string         | string (as is)            |
| Metrics         |        Accuracy, Precision, Recall, F1 Score       |
| Context Format  | Table title & content  | Textual paragraph context |

## Summary of Results

| Metric     | Table-based | Context-based |
|------------|-------------|---------------|
| Accuracy   | 0.0218      | 0.4216        |
| Precision  | 0.0543      | 0.4465        |
| Recall     | 0.0218      | 0.4216        |
| F1 Score   | 0.0243      | 0.4264        |

- The model showed **significantly higher performance** on context-based QA.
- Table-based QA performance was **extremely low**.
- → Likely due to model pretraining on unstructured natural language datasets.

## Interpretation & Implications

- The model is clearly optimized for context-based QA in natural language.
- Performance differences across all metrics were **8–10x**.
- Model architecture and training data have a major influence on generalization.
- Results highlight the need for specialized pretraining on **structured QA data (e.g., tables)**.

## Limitations & Future Directions

- Answer position information was removed from the table-based data during preprocessing, which may have contributed to poor performance.
- Structural differences between datasets limit direct comparisons.
- Only one model was tested; **further studies should compare multiple models**.
- Future work should explore **data-type-specific model design** and **modular evaluation frameworks**.

