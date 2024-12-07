---
{"dg-publish":true,"permalink":"/main/equity-chatbot-folder/notes/qualities-of-a-good-portfolio/"}
---

## Diversification
### Concept
A good portfolio is optimally diversified, i.e. *no eggs reside in one basket*. This can be measured by simple pie charts. Any 
### Python Implementation
```python wrap
market_cap_summary = portfolio_df['Market Cap Size'].value_counts()
    values = market_cap_summary.tolist()
    labels = market_cap_summary.index.tolist()
    fig, ax = plt.subplots(figsize=(10, 10))
    fig.patch.set_alpha(0)  
    ax.pie(
        values,
        labels=labels,
        autopct='%1.1f%%',
        textprops={'color': 'white'},  
        startangle=90
    )
    st.pyplot(fig)
    st.text('Market Cap Distribution')
```
### Concept

### Python Implementation

### Concept

### Python Implementation

### Concept

### Python Implementation

### Concept

### Python Implementation

### Concept

### Python Implementation

### Concept

### Python Implementation

### Concept

### Python Implementation



