---
layout: home
title: Political Analysis Replication Guidelines
---

Political Analysis requires authors of conditionally accepted manuscripts to provide complete replication materials before publication. This ensures that all findings are reproducible.

## **Replication Checklist**
To insure timely replication of your materials, complete the following checklist before submitting your materials.

✔️ **Run File**: A script (e.g., `.R`, `.py`, `.sh`) that executes all analyses in the correct order.  
✔️ **Log File**: A log of the output from a complete run of the analysis, generating by executing the run file.
✔️ **Figures & Outputs**: All tables and figures from the complete run should be included (timestamps for the figures should be consistent with the timestamp for the log file).
✔️ **Compute & Runtime Details**: In the run file, note the approximate runtime for each script, as well as the compute used (number of cores and required RAM).
✔️ **Data & Code**: Clearly documented datasets and analysis scripts.

## **Submission Process**
1. **Prepare**: Organize the replication package, ensuring all components run smoothly.  
2. **Upload**: Submit the package to [Dataverse](https://dataverse.harvard.edu/dataverse/pan) or [Code Ocean](https://codeocean.com/).  
3. **Verify**: The **replication team** will test the materials.  
4. **Approval**: Once verified, the replication is finalized, and the manuscript moves forward.  

## **Best Practices**
- Use **open-source software** whenever possible.
- Include a **README file** following [this template](https://social-science-data-editors.github.io/template_README/).
- Ensure **code is automated**, requiring minimal manual intervention.
- If using **restricted-access data**, provide as much public code as possible.

For full details, visit [Political Analysis Dataverse](https://dataverse.harvard.edu/dataverse/pan).  
For questions, contact: **political.analysis.replications@gmail.com**.

---
