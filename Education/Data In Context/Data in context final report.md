# **Auditing the Quality of Facial Recognition Systems Across Demographic Groups**
## - Animesh Jadhav

## **Introduction**

Facial recognition technology is being increasingly applied to critical domains such as security, recruitment, education, and social media content moderation. As facial recognition technology gathers increasing stakes in societally mediated decision-making processes, concerns over accuracy, fairness, and accountability have become, in turn, increasingly acute. Algorithmic auditing has become a major methodology in responding to these concerns. An audit tests algorithms for performance with respect to different inputs in order to detect systematic inequities which might suggest bias or different treatment with regards to impact (FnT Auditing Algorithms).

In this report, an algorithmic audit of a facial recognition task will be conducted with respect to demographics such as gender, race/ethnicity, and age. Based on a labeled dataset of 1,000 facial images with human-verified demographic information, I will examine if a meaningful disparity in the level of output quality exists among these demographic divisions. The implications of this analysis are important because a demographic performance disparity in facial recognition systems can perpetuate social inequalities based on existing social structures. Through this analysis, a minimal disparity in output quality will be observed among gender divisions, but a dramatic disparity in output quality will be observed among divisions of race/ethnicity and age, which both have implications for demographic performance disparities in facial recognition systems in accordance with previous research findings based on bias in datasets among facial recognition systems (Kärkkäinen & Joo, 2021).

---

## **Data and Methods**

### **Software and Dataset**

The system being audited in this work is a facial analysis model (DeepFace) deployed locally, which takes facial images and predicts a subject’s age, gender, and race. I chose this software because it is widely used in research and practical work, does not require a commercial API to function, and enables complete auditing because it runs locally rather than on a cloud service.

The images have a total of 1,000 facial images with cross-validated labels pertaining to age, gender, and race/ethnicity in an excel sheet. Categories include White, Black, Indian, East Asian, Southeast Asian, Middle Easterners, and Latinos, which correspond rather nicely with those established in the FairFace Dataset.

### **Computational Methods**

Computational methods were used in the audit. Every image in this study went through an analysis using a facial recognition model in order to estimate their age, gender, and racial information. The resulting output was compared to a set of ground truth information in the dataset. Additionally, a rating of each image based on a scale of 1–10 was given based on how accurate the output corresponded to the ground truth.

Evaluation of quality centers on three considerations:

- Age accuracy, calculated using absolute error with respect to predicted age and labeled age range midpoint.
    
- Gender accuracy, evaluated in terms of gender match or mismatch.
    
- Race/ethnicity accuracy, evaluated for a correct or incorrect designation.
    

Disparities in age were punished by stepwise penalties, with errors in gender or racial categorization meriting harsher penalties because of the social significance of these characteristics. Every score came with an accompanying message specifying reasons for subtracting points. Such a subjective method with a pre-set format corresponds with algorithmic auditing logic in literature, with a focus on being transparent rather than objective.

Using this information, quality averages were calculated for each demographic variable considered. Further statistics such as the frequency, minimum, maximum, and standard deviation were calculated to better understand these averages. Differences in these variables make up the basis of analysis presented below.

---

## **Findings**

### **Gender**

The average rating for the quality of female faces in the model is 7.10, in contrast to 7.20 for men. The difference is tiny and clearly in one standard deviation. Therefore, there is a good indication that with a given definition of quality, this model gives equal performance in both directions without any gender bias. Unlike previous systems, which demonstrated a marked gender gap, especially in darker-skinned women, this model does not have a gender performance gap.

### **Race & Ethnicity**

The performance disparity when considering race and ethnicity is more evident. The highest average quality scores were recorded in Black faces with a score of 8.03, followed by White faces with a score of 7.83. Further, East Asian faces with a score of 6.63, Southeast Asian faces with a score of 6.58, and Latino/Hispanic faces with a score of

Such disparities go beyond a full point on a scale of ten, ensuring these are not results of random variability but a systematic disparity in performance. Such a trend is consistent with results obtained in studies using FairFace, which show in their records that facial recognition models tend to generalize ineffectively in underrepresented races in their databases. Although this audit is not capable of isolating an individual training dataset used by this model, these results indicate a continued impact of racial representation and labeling on performance.

### **Age**

The most evident disparities are seen in age disparities. The performance of the model is observed to be best in faces belonging to the age bracket 30–44 years (average 8.03) and 18–29 years (average 7.73). Moreover, in both the lower and higher age ranges, a steep fall in performance is observed. Faces below 18 years average 5.89, while those above

Such a U-shaped pattern reveals that this model is most optimized for middle-aged people and performs badly both at the ends of this distribution and in other people. It is in complete accordance with previous research, which indicated that wrinkles, facial structure, and underdeveloped facial elements can make a negative impact on face analysis models that work mainly with adults.

### **Bias Evaluation**

On aggregate, these findings suggest a performance disparity in demographic outcomes based on race/ethnicity and age but not based on gender. Although the definition of “bias” can be considered in normative and statistical contexts, these findings are systematic and consistent with imbalances in datasets, such as those described in auditing literature.

---

## **Conclusion**

This audit illustrates how algorithms can have very different performance rates among different demographic categories. Although accuracy is not put into question, it appears marked in this case, this particular facial recognition algorithm performs very evenly for both males and females, but not for other racial, especially East Asian, Southeast Asian, and Latino, facial features, nor for children and elderly people.

One such explanation for these results is dataset imbalance. As Kärkkäinen & Joo have stated, machine learning algorithms which have access to an imbalanced dataset, showing a predisposition towards a particular racial and age demographic, will not generalize well towards other demographics because these other demographics are underrepresented.

The age-related disparities may also represent difficulties in estimating age in the tail ends of the age ranges.

The results have important implications. Facial recognition technology is ubiquitously deployed in settings where a mistake can have serious consequences, such as in surveillance, identification, and demographic studies. The presence of disparities in performance over races and ages can potentially perpetuate inequalities. From an auditing literature viewpoint, this work confirms a critical requirement under algorithmic auditing literature—the need to assess not just system accuracy but performance across all groups.

Ultimately, this case serves to illustrate a need for continued research and analysis into facial recognition technology and a need for more well-rounded datasets in order to assess technology in a fair manner. Algorithmic audits are a tool that serves an important function in these efforts.

---

## **Works Cited**

Kärkkäinen, K., & Joo, J. (2021). _FairFace: Face Attribute Dataset for Balanced Race, Gender, and Age for Bias Measurement and Mitigation_. Proceedings of the IEEE/CVF Winter Conference on Applications of Computer Vision.

Kroll, J. et al. (Year). _Auditing Algorithms_. Foundations and Trends in Privacy and Security.