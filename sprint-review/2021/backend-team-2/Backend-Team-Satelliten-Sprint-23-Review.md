# Sprint Review für Sprint #23
## Backend Team "Satelliten"

---

# Jira-Tickets

| ID	   | Title  	                            |
|:-	       |:-	                                    |
| TACO-776 | add-services / X-On-Behalf-Of im AuditLog Service unterstützen |

---

## TACO-776
### add-services / X-On-Behalf-Of im AuditLog Service unterstützen

Um GvLog-Einträge auch aus technischen Prozessen schreiben zu können,
wird in der API nun der optionale Header X-On-Behalf-Of unterstützt.
Wird dieser Header angegeben, so wird der darin übergebene Header in die
Userfelder des GvLog-Eintrages übernommen. Wurde der Header nicht
angegeben, so wird der User aus dem aktuellen Userkontext verwendet.

---
