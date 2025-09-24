These measures track the CQI questions in each category.  By using a switch statement, we first find the "category name" and pair it with the table[column] where the answer would be recorded.

Note: each category has **the same questions.** This can be further simplified if all CQI reviews are done under a "Generic" category.  But, we'd have to add a date field that would capture the old categorical 

>> Does this chart meet PF&R standards?

```dax
Pass_Fail = 
VAR CurrentDate = TODAY()
VAR TargetDate = DATE(2025, 9, 23)
VAR CQIName = RELATED('Dim_CQICategory'[CQI_Name])
RETURN
IF(
    CurrentDate <= TargetDate,
    // BEFORE or ON 9/23/2025 - original logic
    SWITCH(
        CQIName,
        "Burns", RELATED('Dim_CQISupplementalQuestions1'[QA366]),
        "Cardiac Arrest", RELATED('Dim_CQISupplementalQuestions'[QA71]),
        "Diabetic", RELATED('Dim_CQISupplementalQuestions'[QA225]),
        "Generic", RELATED('Dim_CQISupplementalQuestions'[QA144]),
        "Pediatric", RELATED('Dim_CQISupplementalQuestions'[QA201]),
        "Respiratory", RELATED('Dim_CQISupplementalQuestions1'[QA327]),
        "Sepsis", RELATED('Dim_CQISupplementalQuestions'[QA80]),
        "Stroke", RELATED('Dim_CQISupplementalQuestions'[QA171]),
        "Trauma", RELATED('Dim_CQISupplementalQuestions'[QA92]),
        BLANK()
    ),
    // AFTER 9/23/2025 - NEW logic using generic switch
    RELATED('Dim_CQISupplementalQuestions'[QA144])
)

```

---

>> CQI Reviewer Comments

```dax
ReviewerComments = 
VAR CurrentDate = TODAY()
VAR TargetDate = DATE(2025, 9, 23)
VAR CQIName = RELATED('Dim_CQICategory'[CQI_Name])
RETURN
IF(
    CurrentDate <= TargetDate,
    // BEFORE or ON 9/23/2025 - original logic
    SWITCH(
        CQIName,
        "Burns", RELATED('Dim_CQISupplementalQuestions'[QA4]),
        "Cardiac Arrest", RELATED('Dim_CQISupplementalQuestions1'[QA334]),
        "Diabetic", RELATED('Dim_CQISupplementalQuestions'[QA5]),
        "Generic", RELATED('Dim_CQISupplementalQuestions'[QA3]),
        "Pediatric", RELATED('Dim_CQISupplementalQuestions'[QA14]),
        "Respiratory", RELATED('Dim_CQISupplementalQuestions'[QA7]),
        "Sepsis", RELATED('Dim_CQISupplementalQuestions'[QA6]),
        "Stroke", RELATED('Dim_CQISupplementalQuestions'[QA13]),
        "Trauma", RELATED('Dim_CQISupplementalQuestions'[QA15]),
        BLANK()
    ),
    // AFTER 9/23/2025 - NEW logic using generic switch
    RELATED('Dim_CQISupplementalQuestions'[QA3])
)
```

---

>> Were MCEMS protocols followed appropriately?

```dax
ProtocolsFollowed = 
VAR CurrentDate = TODAY()
VAR TargetDate = DATE(2025, 9, 23)
VAR CQIName = RELATED('Dim_CQICategory'[CQI_Name])
RETURN
IF(
    CurrentDate <= TargetDate,
    // BEFORE or ON 9/23/2025 - original logic
    SWITCH(
        CQIName,
        "Burns", RELATED('Dim_CQISupplementalQuestions'[QA20]),
        "Cardiac Arrest", RELATED('Dim_CQISupplementalQuestions'[QA28]),
        "Diabetic", RELATED('Dim_CQISupplementalQuestions'[QA21]),
        "Generic", RELATED('Dim_CQISupplementalQuestions'[QA24]),
        "Pediatric", RELATED('Dim_CQISupplementalQuestions'[QA26]),
        "Respiratory", RELATED('Dim_CQISupplementalQuestions'[QA23]),
        "Sepsis", RELATED('Dim_CQISupplementalQuestions'[QA22]),
        "Stroke", RELATED('Dim_CQISupplementalQuestions'[QA25]),
        "Trauma", RELATED('Dim_CQISupplementalQuestions'[QA27]),
        BLANK()
    ),
    // AFTER 9/23/2025 - NEW logic using generic switch
    RELATED('Dim_CQISupplementalQuestions'[QA24])
)
```


```dax
Pass_Fail = 
VAR CurrentDate = TODAY()
VAR TargetDate = DATE(2025, 9, 23)
VAR CQIName = RELATED('Dim_CQICategory'[CQI_Name])
RETURN
IF(
    CurrentDate <= TargetDate,
    // BEFORE or ON 9/23/2025 - original logic
    SWITCH(
        CQIName,
        "Burns", RELATED('Dim_CQISupplementalQuestions1'[QA366]),
        "Cardiac Arrest", RELATED('Dim_CQISupplementalQuestions'[QA71]),
        "Diabetic", RELATED('Dim_CQISupplementalQuestions'[QA225]),
        "Generic", RELATED('Dim_CQISupplementalQuestions'[QA144]),
        "Pediatric", RELATED('Dim_CQISupplementalQuestions'[QA201]),
        "Respiratory", RELATED('Dim_CQISupplementalQuestions1'[QA327]),
        "Sepsis", RELATED('Dim_CQISupplementalQuestions'[QA80]),
        "Stroke", RELATED('Dim_CQISupplementalQuestions'[QA171]),
        "Trauma", RELATED('Dim_CQISupplementalQuestions'[QA92]),
        BLANK()
    ),
    // AFTER 9/23/2025 - NEW logic using generic switch
    RELATED('Dim_CQISupplementalQuestions'[QA144])
)
```


---

⚠️ This question has been deactivated and is not longer asked in CQI reviews...

>> Is the narrative well-written and clearly depict all expected EMS activity on-scene?

```dax

```