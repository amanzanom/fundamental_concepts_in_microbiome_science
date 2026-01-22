# Part 3: Annotation of a "typical" IS element (together)

## Annotate ISCca4
For this part we will revisit the transposase `ISCca4` from *Cardinium* bacteria. So, let's go ahead and download the [`ISCca4.fasta`](./data/ISCca4.fasta) (right click 🖱️, open in new tab, then hit the "Dowload raw file" button at the top-right of the viewer).

- Drag the downloaded file (`ISCca4.fasta`) into UGENE or open it (Top-left corner `File -> Open`).

  ![](./images/UGENE/3.01_UGENE_annot_ISCca4_sequence.png)
  <br/><br/>

  - Click on the "Select sequence region" button (<img src="./images/UGENE/UGENE_select_button.png" height="17" title="Select sequence region">).

    ![](./images/UGENE/3.02_UGENE_annot_ISCca4_sequence_select.png)
    <br/><br/>

  - We can choose any range from 1 - n (n= maximun length of sequence). By default, we get from start to end, unless we preselect manually a certain range. Let's then proceed and hit that <img src="./images/UGENE/UGENE_go_button.png" height="17">  button.

    ![](./images/UGENE/3.03_UGENE_annot_ISCca4_sequence_range.png)
    <br/><br/>

- Now lets copy that sequence (press <kbd>Ctrl + C</kbd> ⌨️) and paste it (press <kbd>Ctrl + V </kbd> ⌨️) into ISfinder's BLAST's (`blastx`) search box.

  ![](./images/UGENE/3.04_ISfinder_blast_ISCca4_sequence.png)
  <br/><br/>

  - We then go to the top hit (`ISCca4`) and click on the bit score (`511` 🖱️).

    ![](./images/UGENE/3.05_ISfinder_blast_ISCca4_sequence_topHit.png)
    <br/><br/>

  - Now let's look at the alignment.
    - Did we detect a transposase gene?
    - Which family?
    - Is it complete?
    - Are we dealing with the same transposase?
    
    ![](./images/UGENE/3.06_ISfinder_blast_ISCca4_sequence_align.png)
    <br/><br/>

### CDS
<details>
  
  <summary>See more</summary>
  
  - Back in UGENE, let's now annotate the transposase gene.
    - First, let's use gain that "Select sequence region" button (<img src="./images/UGENE/UGENE_select_button.png" height="17" title="Select sequence region">) and input the range of the BLAST hit (`112 - 982`).

      ![](./images/UGENE/3.07_UGENE_annot_ISCca4_select_hit.png)
      <br/><br/>

    - Transposase gene start: `MNVEKLVEI...`. Does it look good?

      ![](./images/UGENE/3.08_UGENE_annot_ISCca4_select_hit_start.png)
      <br/><br/>

    - Transposase gene end: `...TNIYMTGSQ`. Does it look good?

      ![](./images/UGENE/3.09_UGENE_annot_ISCca4_select_hit_end.png)
      <br/><br/>

    - Let's modify the end so that it includes the stop codon (*) to `112 - 993` using the "Select sequence region" button (<img src="./images/UGENE/UGENE_select_button.png" height="17" title="Select sequence region">).

      ![](./images/UGENE/3.10_UGENE_annot_ISCca4_select_hit_modifyRange.png)
      <br/><br/>

    - We have now the whole coding sequence (CDS)* selected.

      ![](./images/UGENE/3.11_UGENE_annot_ISCca4_select_hit_correct.png)
      \** CDS: portion of a gene that is translated into protein. It begins with a start codon (ATG, GTG, TTG) and ends with a stop codon (*).
      <br/><br/>

    - Let's click (<kbd>Ctrl + N</kbd>) 🖱️. This will open the "Create Annotation" window. We will select `CDS` from the "Annotation type" menu, and write `CDS` in both "Group name" and "Annotation name" fields. Now let's click <img src="./images/UGENE/UGENE_create_button.png" height="17"> 🖱️.

      ![](./images/UGENE/3.12_UGENE_annot_ISCca4_CDS_create.png)
      <br/><br/>

    - We have our first CDS!

      ![](./images/UGENE/3.13_UGENE_annot_ISCca4_CDS_feature.png)
      <br/><br/>

    - Now, time to add some qualifiers (additional fields to the `CDS` feature). This is achieved by selecting the `CDS` and then pressing <kbd>Insert</kbd> ⌨️. You will get an "Add new qualifier" pop-up window to type in: 
      - Name: `codon_start`, Value: `1`.
    
        ![](./images/UGENE/3.14_UGENE_annot_ISCca4_CDS_codonStart_create.png)
        <br/><br/>

      - Name: `transl_table`, Value: `11`.

        ![](./images/UGENE/3.15_UGENE_annot_ISCca4_CDS_translTable_create.png)
        <br/><br/>

      - Name: `product`, Value: `Transposase ISCca4, IS982 family`.

        ![](./images/UGENE/3.16_UGENE_annot_ISCca4_CDS_product_create.png)
        <br/><br/>

      - Name: `translation`, Value: `MNVEKLVEIYYAVDEFLIKFMPYMEKQLLTNSKRKPTRTCSLTLSEIMTVLIAFHVIGFRNFKSYYIHLQQFHSSKFGKLVRYNRFIELIQRTLVPLYCFTQSLSKTKTGCYFMDATAIKVCHIKRAYTHRVFKSIATKGKTSIGWFFGLKLHLIVNDLGEIMNFQLTTGKTNDRLPVENLCKHFMGKMFADKGYISKDLFEKLIEKGVELITQIRKNMKNAFMPLWDKLMLRKRSIIETIIDQLKNISQIEHSRHRSIPNFLVNLIAGITAYALKEKKPSITNIYMTGSQYV`.
        To paste translation in the "Value" field (<kbd>Ctrl + V</kbd> ⌨️), with the `CDS` feature selected, first copy the translation of the feature (press <kbd>Ctrl + T</kbd> ⌨️).

        ![](./images/UGENE/3.17_UGENE_annot_ISCca4_CDS_tranlsation_create.png)
        <br/><br/>

    - Great work! Now, our transposase gene is annotated!

      ![](./images/UGENE/3.18_UGENE_annot_ISCca4_CDS_wQuals.png)

</details>

---

### Repeats
What about the repeats? How would you go about discovering if this transposase is flanked or not by inverted/direct repeats?

#### Direct repeats
<details>
  
  <summary>See more</summary>
  
  - First, lets grab the first 10 and last 10 nucleotides to search for **direct repeats**. We can do this using the "Select sequence region" button (<img src="./images/UGENE/UGENE_select_button.png" height="17" title="Select sequence region">) 🖱️, setting the ranges `1..10` and `1003..1012` and then clicking <img src="./images/UGENE/UGENE_go_button.png" height="17"> 🖱️. Once region is selected, press <kbd>Ctrl + C</kbd> ⌨️ to copy.

    NOTE: In this case, we are working with a full transposase gene. Usually, it makes more sense to search for inverted repeats first, as they are longer.
    
    ![](./images/UGENE/3.19_UGENE_annot_ISCca4_DR_select_start.png)
    <br/>
 
    ![](./images/UGENE/3.20_UGENE_annot_ISCca4_DR_select_end.png)
    <br/><br/>

  - We can go ahead and align these sequences, but it makes more sense to visually inspect them.
   
    Solution 1:
    
    ```
    --------TAATAACCTA # start
    GAGGTTAATA-------- # end
    ```
    
    Solution 2:
    
    ```
    -----TAATAACCTA # start
    GAGGTTAATA----- # end
    ```
    
    Any others?
    <br/><br/>

  - To create the annotations, manually select the direct repeats at the start (`1 - 5`) and end (`1008 - 1012`) of the sequence. For each, press <kbd>Ctrl + N</kbd> ⌨️. This will open the "Create Annotation" window. We will select `repeat_region` from the "Annotation type" menu, and write `repeat_region` in both "Group name" and "Annotation name" fields. Now let's click <img src="./images/UGENE/UGENE_create_button.png" height="17"> 🖱️.
    
    ![](./images/UGENE/3.21_UGENE_annot_ISCca4_DR_create.png)
    <br/><br/>
 
  - As with `CDS`, we need to add some qualifiers. This is achieved by selecting the `repeat_region` and then pressing <kbd>Insert</kbd> ⌨️. You will get an "Add new qualifier" pop-up window to type in: 
    - Name: `rpt_type`, Value: `DIRECT`.
    
      ![](./images/UGENE/3.22_UGENE_annot_ISCca4_DR_rptType_create.png)
      <br/><br/>

    - Name: `note`, Value: `target site duplication generated by insertion of ISCca10`.

      ![](./images/UGENE/3.23_UGENE_annot_ISCca4_DR_note_create.png)
      <br/><br/>
 
  - Now, let's repeat the process for the right-flanking direct repeat.

</details>

---

#### Inverted repeats
<details>
  
  <summary>See more</summary>
  
  - To the **inverted repeats**! lets grab the first 30 and last 30 nucleotides after and before the annotated direct repeats. We can do this using the "Select sequence region" button (<img src="./images/UGENE/UGENE_select_button.png" height="17" title="Select sequence region">) 🖱️, setting the ranges `6 - 35` and `978 - 1007` and then clicking <img src="./images/UGENE/UGENE_go_button.png" height="17"> 🖱️. Once region is selected, press <kbd>Ctrl + C</kbd> ⌨️ to copy the forward region (left) and <kbd>Ctrl + Shift + C</kbd> ⌨️ to copy the reverse complement of the reverse region (right).
    
    ![](./images/UGENE/3.24_UGENE_annot_ISCca4_IR_IRL_select.png)
   
    Press <kbd>Ctrl + C</kbd> ⌨️
    <br/>
    
    ![](./images/UGENE/3.25_UGENE_annot_ISCca4_IR_IRR_select.png)
    
    Press <kbd>Ctrl + Shift + C</kbd> ⌨️
    <br/>

  - We can go ahead and align these sequences. So let's go to the [T-COFEE](https://tcoffee.crg.eu/apps/tcoffee/do:mcoffee) website and paste the IRL and IRR region sequences.

    ![](./images/UGENE/3.26_TCOFEE_align_ISCca4_IRL_vs_IRR_run.png)
    <br/>

    - Lets look at the result. What is the sequence of the inverted repeat?

      ![](./images/UGENE/3.27_TCOFEE_align_ISCca4_IRL_vs_IRR_result.png)
   
      ** ACCT(A/C)AGTTCGGGATTAG
      <br/>
   
    - How does this compare to the inverted repeat sequence of [`ISCca4`](https://isfinder.biotoul.fr/scripts/ficheIS.php?name=ISCca4)?
      
      ```
      ACCTAAGTTCGGGATTAG  # our IRL
      ACCTCAGTTCGGGATTAG  # our IRR
      ACGTCAGTTTTGGATTAGA # ISCca4 IRL (ISfinder, length 18/19)
      ACGTGAGTTTCGGATTAGA # ISCca4 IRR (ISfinder, length 18/19)
      ** * ****  *******  # sequence match
      ```
      <br/>
    
  - To create the annotations, use the search box in UGENE copy and pasting the identidied sequences for IRL (`ACCTAAGTTCGGGATTAG`) and IRR (`ACCTCAGTTCGGGATTAGA`).
    
    ![](./images/UGENE/3.28_UGENE_search_ISCca4_IRL_result.png)
    <br/><br/>

  - After pasting, search will be automatic and region will be selected. For each, press <kbd>Ctrl + N</kbd> ⌨️. This will open the "Create Annotation" window. We will select `repeat_region` from the "Annotation type" menu, and write `repeat_region` in both "Group name" and "Annotation name" fields. Now let's click <img src="./images/UGENE/UGENE_create_button.png" height="17"> 🖱️.

    ![](./images/UGENE/3.29_UGENE_search_ISCca4_IRL_annot.png)
    <br/><br/>

    **\*Note:** For IRR, make sure to check the <img src="./images/UGENE/UGENE_complement_button.png" height="17"> field.

    ![](./images/UGENE/3.30_UGENE_search_ISCca4_IRR_annot.png)
    <br/><br/>
 
  - As with `CDS`, we need to add some qualifiers. This is achieved by selecting the `repeat_region` and then pressing <kbd>Insert</kbd>. You will get an "Add new qualifier" pop-up window to type in: 
    - Name: `rpt_type`, Value: `INVERTED`.
      
      ![](./images/UGENE/3.31_UGENE_search_ISCca4_IRR_annot_qual_rptType.png)
      <br/><br/>

    - Name: `note`, Value: `ISCca4, terminal inverted repeat IRL`.
      
      ![](./images/UGENE/3.32_UGENE_search_ISCca4_IRR_annot_qual_note.png)
      <br/><br/>
 
  - Now, let's annotate the other inverted repeat (IRR) in a similar fashion.

</details>

---

#### Mobile element feature
<details>
  
  <summary>See more</summary>
  Your current annotation should look somehting like this

  ![](./images/UGENE/3.33_UGENE_ISCca4_allFeatures.png)
  <br/><br/>
  
  - Now that we have all features of the IS element annotated, we group them inside a `mobile_element` feature. For this, lets choose a range that covers all the mobile element, in this case, from IRL to IRR (`1 - 1012`) and click <img src="./images/UGENE/UGENE_go_button.png" height="17"> 🖱️.

    ![](./images/UGENE/3.34_UGENE_ISCca4_ME_search.png)
    <br/><br/>
    
  - Once the region is selected, press <kbd>Ctrl + N</kbd> ⌨️. This will open the "Create Annotation" window. We will select `mobile_element` from the "Annotation type" menu, and write `mobile_element` in both "Group name" and "Annotation name" fields. Now let's click <img src="./images/UGENE/UGENE_create_button.png" height="17"> 🖱️.

    ![](./images/UGENE/3.35_UGENE_ISCca4_ME_annot.png)
    <br/><br/>
 
  - As with `CDS` and `repeat_region`, we need to add some qualifiers. This is achieved by selecting the `mobile_element` and then pressing <kbd>Insert</kbd>. You will get an "Add new qualifier" pop-up window to type in: 
    - Name: `mobile_element_type`, Value: `insertion sequence:ISCca4`.
      
      ![](./images/UGENE/3.36_UGENE_ISCca4_ME_annot_MEtype.png)
      <br/><br/>

    - Name: `rpt_family`, Value: `IS982`.
      
      ![](./images/UGENE/3.37_UGENE_ISCca4_ME_annot_rptFamily.png)
      <br/><br/>
      
    - Name: `rpt_type`, Value: `DISPERSED`.
      
      ![](./images/UGENE/3.38_UGENE_ISCca4_ME_annot_rptType.png)
      <br/><br/>
 
  - Done! Your annotaiton should look as follows.
    
    ![](./images/UGENE/3.39_UGENE_ISCca4_ME_annot_final.png)

</details>

---

#### Exporting to GenBank format
<details>
  
  <summary>See more</summary>
  Now that we are done, we do not want to loose our work. So, let's go ahead and export the sequence along with the annotation in two simple steps
  
  - First, go to the left panel and find the sequence feature (`ISCca4.fasta` if you opened the file). Right click 🖱️ and go to `Export/Import -> Export sequences...`.

    ![](./images/UGENE/3.40_UGENE_ISCca4_ME_annot_final_export.png)
    <br/><br/>
    
  - Set the name of the output file to `ISCca4.gb` and select `GenBank` form the "File format to use" drop-down menu. Now click <img src="./images/UGENE/UGENE_export_button.png" height="17"> 🖱️.

    ![](./images/UGENE/3.41_UGENE_ISCca4_ME_annot_final_export_gbkFile.png)
    <br/><br/>
 
  - Done!

  🥳 Congrats! If you made it all the way down here, you succesfuly annotated your first IS element! 🥳

</details>

---

## Further reading
**INSDC feature table:** [https://www.insdc.org/submitting-standards/feature-table/](https://www.insdc.org/submitting-standards/feature-table/).

ISfinder's *General Information* tab: [https://isfinder.biotoul.fr/general_information.php](https://isfinder.biotoul.fr/general_information.php).
<br/>

<p align="right">
    <kbd> <br> <a href="./Part_4.md"><big><b>Next: Part 4</b></big></a> <br> </kbd>
</p>
