---
{"dg-publish":true,"permalink":"/main/equity-chatbot-folder/notes/bug-and-errors/"}
---

## All errors shall be documented in a checkbox format 
Resolved errors shall be "Checked away when resolved", do not delete error logs. 


- [x] Out of Bounds Error when time frame exceeds period of incorporation. 
	- Fix: Period defaults to 'Max' if DOI exceeds the given time frame. 
- [ ] Company information not being retrieved properly for some stocks. Will have to add an error statement for that. 
- [ ] LSE Stock data is not being translated properly
- [ ] Risk free rate is assumed to be 7.635% (Indian). More granular controls have to be set for better accuracy. 
- [ ] 