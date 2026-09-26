# Implement Client Script & UI Policy (Incident)

> ServiceNow Developer Project - Completed on Personal Developer Instance

## 📌 Project Overview
This project implements UI Policy and Client Scripts on the Incident table to control form behavior client-side.

## 🎯 UI Policy: High Impact Control

- **Table:** Incident `[incident]`
- **Name:** High Impact Control
- **Condition:** `Impact is 1 - High`
- **Reverse if false:** true

### UI Policy Actions:
1.  **Assignment Group** -> Mandatory = `true`
2.  **Urgency** -> Read Only = `true`

## 💻 Client Scripts

### 1. onChange - Auto set Urgency
**When Impact changes to High, auto-set Urgency to High**
```javascript
function onChange(control, oldValue, newValue, isLoading) {
  if (isLoading || newValue == '') return;
  if (newValue == '1') {
    g_form.setValue('urgency', '1');
    g_form.addInfoMessage('Urgency set to High due to High Impact');
  }
}
