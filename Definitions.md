In survival analysis, you typically use the time-to-event data to estimate survival probabilities over time. In the tcga_clinical collection we have:
1. "vital_status": This variable indicates whether the patient is alive or dead.
2. "days_to_last_followup": This variable provides the number of days from diagnosis to the last follow-up for patients who are still alive. However, for patients who are deceased, this field is empty.
3. "days_to_birth": This variable represents the number of days from birth to diagnosis. 
4. In the tcga_rna_seq collection we also have "days_to_diagnosis" 

Here is the method you can use to do time-to-event analysis using models such as CoxPH:
 
Since you are interested in analyzing survival probabilities, you should focus on the "vital_status" and "days_to_last_followup" variables. Here's how you can proceed:
1. Define the event and censoring times:
    * For patients who are alive (vital_status = Alive), you will use "days_to_last_followup" as the event time. This represents the time from diagnosis to the last follow-up.
    * For patients who are deceased (vital_status = Dead), you will consider them as events, and you will not use "days_to_last_followup" for these patients since it's empty. Instead, you will use the time from diagnosis to death as the event time. (You would calculate the time from diagnosis to death as follows: {Time from diagnosis to death} = {death_date} - {diagnosis_date})
2. Perform survival analysis:
    * You can use techniques such as Kaplan-Meier curves and Cox proportional hazards models to analyze survival probabilities and assess the impact of covariates on survival outcomes.
    * Patients who are still alive at the end of the study or lost to follow-up are considered censored observations. Their survival times 

Just to have a experiment, you can consider these covariates as BCL9 expression (its ID in our data is "ENSG00000116128.11"), age, tumor stage, and hormone receptor status, etc. on survival outcomes using CoxPH

**What is mRNA?**

Plays a crucial role in the process of converting genetic information from DNA into proteins, a process known as protein syntehsis.

Simply, 

mRNA as a messenger in your body's cellular process, delivering important instructions from DNA, which is like a big blueprint for your body. DNA holds all the information needed to make everything in your body, but it stays safely inside the nucleus of the cell, kind of like a library that houses all the original copies of blueprints.

When your body needs to make a protein, which is a building block for everything from muscles to enzymes, it doesn't want to take the original blueprint out of the library. Instead, it makes a copy of the part of the blueprint that's needed — this copy is the mRNA.

Here's what happens in three simple steps:

**Copying the Instructions:** Inside the cell's nucleus, the DNA blueprint for a specific protein is copied onto the mRNA molecule.
**Sending the Message:** This mRNA then leaves the nucleus and goes into the main part of the cell, carrying the instructions on how to make the protein.
**Building the Product:** The cell has little factories called ribosomes that read the instructions on the mRNA and use them to put together the protein, piece by piece, like building a model from a kit based on the instructions.
In summary, mRNA is how your body safely copies and uses the vital instructions from DNA to make the proteins necessary for life, without risking damage to the original DNA blueprints.

**What is BCL9?**  
BCL9 is a gene in humans that's similar to a gene in fruit flies involved in developing their body segments. It was first discovered because of its unusual placement in the DNA of a person with a type of leukemia, a blood cancer.

**What does BCL9 do?**  
In normal situations, BCL9 works as part of a team in a pathway called Wnt, which is crucial for cell growth and development. It specifically helps to turn on certain genes that the Wnt pathway controls by sticking to a protein called β-catenin. However, BCL9 can be a bit of a troublemaker in cancer. It's been found in higher amounts in many different cancers, often where it shouldn't be, leading to poor outcomes in these diseases.

**How does it relate to cancer?**  
1. **Increased BCL9 is bad**: Research has shown that when there are more copies of BCL9 or it is overly active, it's usually linked with a worse prognosis in cancer patients.
2. **MicroRNAs and BCL9**: MicroRNAs, which help regulate how much of a protein is made from genes, are often less active in cancers, leading to more BCL9 than needed. 
3. **Other proteins**: Some proteins that normally help keep BCL9's role in cancer in check are often less abundant in tumors.
4. **Blocking BCL9 is good**: Studies have found that stopping BCL9 from working with β-catenin can help reduce tumor growth.

**BCL9’s flexibility in roles**: While mostly known for its role in the Wnt pathway, BCL9 has other jobs too:
- It doesn’t affect lens development in mice when part of it is removed.
- It functions independently of β-catenin in making dental enamel.
- It interacts with proteins that are influenced by hormones like estrogen and androgen.
- A certain altered form of BCL9, found in severe cases of leukemia, doesn’t even include the part that normally binds to β-catenin.

**Novel discoveries in this study**:
- The study discovered a new cancer-related role for BCL9. It interacts with paraspeckle proteins, which are involved in regulating what happens to RNA after it’s made. This interaction helps stabilize RNA for genes that are important in calcium signaling and neuron-like communication in certain aggressive types of colorectal cancer, giving these cancer cells a better ability to 'talk' to each other, which can contribute to the cancer’s growth and spread.

In essence, while BCL9 normally has a specific role in cellular development and growth, it can become harmful in cancer, promoting tumor growth and worsening the disease's prognosis. The new findings about its interaction with paraspeckle proteins open up potential new avenues for targeted cancer treatments.


 **What is RNA-Seq?**
 A technique that reads the RNA to see which genes are active (or "expressed") in cells.

* PyCaret is an open-source Python library that is designed to facilitate and streamline the machine learning workflow. 
* It provides a high-level interface and automates various steps involved in building, training, evaluating, and deploying machine learning models. 
* It is useful to quickly experiment with different algorithms, compare their performance, and build predictive models without writing extensive code.

