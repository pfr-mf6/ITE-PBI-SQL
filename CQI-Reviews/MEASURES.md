These measures track the CQI questions in each category.  By using a switch statement, we first find the "category name" and pair it with the table[column] where the answer would be recorded.

Note: each category has **the same questions.** This can be further simplified if all CQI reviews are done under a "Generic" category.  But, we'd have to add a date field that would capture the old categorical 

>> Does this chart meet PF&R standards?

```dax
Pass_Fail = 
SWITCH(
    RELATED('Dim_CQICategory'[CQI_Name]),
    "Burns", RELATED('Dim_CQISupplementalQuestions1'[QA354]),
    "Cardiac Arrest", RELATED('Dim_CQISupplementalQuestions'[QA137]),
    "Diabetic", RELATED('Dim_CQISupplementalQuestions'[QA193]),
    "Generic", RELATED('Dim_CQISupplementalQuestions'[QA16]),
    "Pediatric", RELATED('Dim_CQISupplementalQuestions'[QA51]),
    "Respiratory", RELATED('Dim_CQISupplementalQuestions1'[QA304]),
    "Sepsis", RELATED('Dim_CQISupplementalQuestions'[QA77]),
    // "STEMI", RELATED('Dim_CQISupplementalQuestions'[QA192]),
    "Stroke", RELATED('Dim_CQISupplementalQuestions'[QA18]),
    "Trauma", RELATED('Dim_CQISupplementalQuestions'[QA13]),
    BLANK()
)

```

---

>> CQI Reviewer Comments

```dax
ReviewerComments = 
SWITCH(
    RELATED('Dim_CQICategory'[CQI_Name]),
    "Burns", RELATED('Dim_CQISupplementalQuestions'[QA5]),
    "Cardiac Arrest", RELATED('Dim_CQISupplementalQuestions'[QA17]),
    "Diabetic", RELATED('Dim_CQISupplementalQuestions'[QA6]),
    "Generic", RELATED('Dim_CQISupplementalQuestions'[QA4]),
    "Pediatric", RELATED('Dim_CQISupplementalQuestions'[QA12]),
    "Respiratory", RELATED('Dim_CQISupplementalQuestions'[QA9]),
    "Sepsis", RELATED('Dim_CQISupplementalQuestions'[QA8]),
    //"STEMI", RELATED('Dim_CQISupplementalQuestions'[QA192]),
    "Stroke", RELATED('Dim_CQISupplementalQuestions'[QA10]),
    "Trauma", RELATED('Dim_CQISupplementalQuestions'[QA14]),
    BLANK()
)
```

---

>> Were MCEMS protocols followed appropriately?

```dax
ProtocolsFollowed = 
-- Were MCEMS protocols followed appropriately?
SWITCH(
    RELATED('Dim_CQICategory'[CQI_Name]),
    "Burns", RELATED('Dim_CQISupplementalQuestions'[QA24]),
    "Cardiac Arrest", RELATED('Dim_CQISupplementalQuestions'[QA35]),
    "Diabetic", RELATED('Dim_CQISupplementalQuestions'[QA25]),
    "Generic", RELATED('Dim_CQISupplementalQuestions'[QA29]),
    "Pediatric", RELATED('Dim_CQISupplementalQuestions'[QA32]),
    "Respiratory", RELATED('Dim_CQISupplementalQuestions'[QA28]),
    "Sepsis", RELATED('Dim_CQISupplementalQuestions'[QA26]),
    "Stroke", RELATED('Dim_CQISupplementalQuestions'[QA31]),
    "Trauma", RELATED('Dim_CQISupplementalQuestions'[QA34]),
    BLANK()
)
```


---

⚠️ This question has been deactivated and is not longer asked in CQI reviews...

>> Is the narrative well-written and clearly depict all expected EMS activity on-scene?

```dax

```