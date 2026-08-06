# JavaScript Data Transformation using Code Node

## Project Name
JavaScript Data Transformation using n8n Code Node

## Objective
The objective of this project is to use the n8n Code node to transform a messy dataset using JavaScript. The workflow normalizes names, converts email addresses to lowercase, calculates grades based on scores, and filters the dataset to keep only Grade A and Grade B records.

---

## Workflow

Manual Trigger → Code Node

---

## Features

- Normalize names (trim spaces and convert to Title Case)
- Convert email addresses to lowercase
- Calculate grades using JavaScript
- Filter records using `.filter()`
- Return only Grade A and Grade B records

---

## Technologies Used

- n8n
- JavaScript
- Code Node

---

## Code Node Script

```javascript
const data = [
  { name: "  noor-ul-huda ", email: "NOOR@EXAMPLE.COM", score: 92 },
  { name: "ali KHAN", email: "ALI@EXAMPLE.COM", score: 85 },
  { name: " sara ahmed ", email: "SARA@EXAMPLE.COM", score: 78 },
  { name: "HAMZA", email: "HAMZA@EXAMPLE.COM", score: 65 },
  { name: " ayesha ", email: "AYESHA@EXAMPLE.COM", score: 55 },
  { name: "usman ali", email: "USMAN@EXAMPLE.COM", score: 88 },
  { name: " FATIMA ", email: "FATIMA@EXAMPLE.COM", score: 73 },
  { name: "zain", email: "ZAIN@EXAMPLE.COM", score: 81 },
  { name: "MARYAM", email: "MARYAM@EXAMPLE.COM", score: 69 },
  { name: " hassan ", email: "HASSAN@EXAMPLE.COM", score: 95 },
  { name: "amna", email: "AMNA@EXAMPLE.COM", score: 84 },
  { name: "bilal", email: "BILAL@EXAMPLE.COM", score: 58 },
  { name: "iqra", email: "IQRA@EXAMPLE.COM", score: 76 },
  { name: "DANIYAL", email: "DANIYAL@EXAMPLE.COM", score: 90 },
  { name: "maham", email: "MAHAM@EXAMPLE.COM", score: 62 }
];

function titleCase(str) {
  return str
    .trim()
    .toLowerCase()
    .split(" ")
    .map(word => word.charAt(0).toUpperCase() + word.slice(1))
    .join(" ");
}

const transformed = data.map(person => {
  let grade;

  if (person.score >= 90) grade = "A";
  else if (person.score >= 80) grade = "B";
  else if (person.score >= 70) grade = "C";
  else if (person.score >= 60) grade = "D";
  else grade = "F";

  return {
    name: titleCase(person.name),
    email: person.email.toLowerCase(),
    score: person.score,
    grade
  };
});

const filtered = transformed.filter(person =>
  person.grade === "A" || person.grade === "B"
);

return filtered.map(item => ({
  json: item
}));
```

---

## Before Sample Data

| Name | Email | Score |
|------|-------|------:|
| noor-ul-huda | NOOR@EXAMPLE.COM | 92 |
| ali KHAN | ALI@EXAMPLE.COM | 85 |
| sara ahmed | SARA@EXAMPLE.COM | 78 |
| HAMZA | HAMZA@EXAMPLE.COM | 65 |
| ayesha | AYESHA@EXAMPLE.COM | 55 |

---

## After Sample Data

| Name | Email | Score | Grade |
|------|-------|------:|:-----:|
| Noor-ul-Huda | noor@example.com | 92 | A |
| Ali Khan | ali@example.com | 85 | B |
| Usman Ali | usman@example.com | 88 | B |
| Zain | zain@example.com | 81 | B |
| Hassan | hassan@example.com | 95 | A |
| Amna | amna@example.com | 84 | B |
| Daniyal | daniyal@example.com | 90 | A |

---

## Conclusion

This project demonstrates how JavaScript can be used inside the n8n Code node to transform data efficiently. It cleans names, standardizes email addresses, calculates grades, and filters records using JavaScript array methods such as `.map()` and `.filter()`. The workflow produces a clean and organized dataset suitable for further automation.

---
