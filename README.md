# Automation-tassk-web-tables
## Website used for testcase 
URL-https://assertqa.com/practice/webtables
## Testcase
```
from selenium import webdriver
from selenium.webdriver.common.by import By

driver = webdriver.Chrome()
driver.get("https://assertqa.com/practice/webtables")

headers = driver.find_elements(By.TAG_NAME, "th")

for header in headers:
    print(header.text)


rows = driver.find_elements(By.XPATH, "//table/tbody/tr")

if rows:
    print("First row:", rows[0].text)
else:
    print("No data rows found")

rows = driver.find_elements(By.XPATH, "//table/tbody/tr")

if rows:
    print("Last row:", rows[-1].text)
else:
    print("No data rows found")

search = driver.find_element(
    By.XPATH, "//input[@placeholder='Search by name, email...']"
)
search.send_keys("Smith")

rows = driver.find_elements(By.XPATH, "//table/tbody/tr")

for row in rows:
    if "Smith" in row.text:
        print("Matching record:", row.text)

rows = driver.find_elements(By.XPATH, "//table/tbody/tr")

for row in rows:
    cells = row.find_elements(By.TAG_NAME, "td")
    for cell in cells:
        if "@" in cell.text:
            print(cell.text)
headers = driver.find_elements(By.TAG_NAME, "th")
names = [h.text.strip() for h in headers]

if "Due" not in names:
    print("Due column not found")
else:
    index = names.index("Due")
    rows = driver.find_elements(By.XPATH, "//table/tbody/tr")
    records = []

    for row in rows:
        cells = row.find_elements(By.TAG_NAME, "td")
        if len(cells) > index:
            due = float(cells[index].text.replace("$", "").replace(",", ""))
            records.append((due, row.text))

    if records:
        print("Highest Due:", max(records))


links = driver.find_elements(By.TAG_NAME, "a")

if links:
    print("PASS - Website link exists")
    for link in links:
        print(link.text, link.get_attribute("href"))
else:
    print("FAIL - No links found")
rows = driver.find_elements(By.XPATH, "//table/tbody/tr")

print("Total data rows:", len(rows))
driver.quit()
```
## Output

<img width="1046" height="600" alt="image" src="https://github.com/user-attachments/assets/39b1a09b-4d50-43d7-9805-f1c109fa2adb" />
<img width="676" height="241" alt="image" src="https://github.com/user-attachments/assets/a503da57-f457-42b3-b363-c66c67801628" />

