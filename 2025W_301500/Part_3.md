# Part 3: Annotation of a "typical" IS element (together)
👷🏽🏗️ Under construction....

## Annotate ISCca4
For this part we will revisit the transposase `ISCca4` from *Cardinium* bacteria. So, let's go ahead and download the [`ISCca4.fasta`](./data/ISCca4.fasta) (right click 🖱️ and download).

- Drag the downloaded file (`ISCca4.fasta`) into UGENE or open it (Top-left corner `File -> Open`).

  ![](./images/UGENE/3.01_UGENE_annot_ISCca4_sequence.png)
  <br/><br/>

  - Click on the "Select sequence region" button (<img src="./images/UGENE/UGENE_select_button.png" height="17" title="Select sequence region">).

    ![](./images/UGENE/3.02_UGENE_annot_ISCca4_sequence_select.png)
    <br/><br/>

  - We can choose any range from 1 - n (n= maximun length of sequence). By default, we get from start to end, unless we preselect manually a certain range. Let's then proceed and hit that <img src="./images/UGENE/UGENE_go_button.png" height="17">  button.

    ![](./images/UGENE/3.03_UGENE_annot_ISCca4_sequence_range.png)
    <br/><br/>

- Now lets copy that sequence (<kbd>Ctrl + C</kbd>) and paste it (<kbd>Ctrl + V </kbd>) into ISfinder's BLAST's (`blastx`) search box.

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

  - Now, time to add some qualifiers (additional fields to the `CDS` feature). This is achieved by selecting the `CDS` and then clicking <kbd>Insert</kbd>. You will get an "Add new qualifier" pop-up window to type in: 
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
      To paste translation in the "Value" field (<kbd>Ctrl + V</kbd>), with the `CDS` feature selected, copy the translation of the feature.

      ![](./images/UGENE/3.17_UGENE_annot_ISCca4_CDS_tranlsation_create.png)
      <br/><br/>

  - Great! Now, our transposase gene is annotated!

    ![](./images/UGENE/3.18_UGENE_annot_ISCca4_CDS_wQuals.png)
    <br/><br/>

  - What about the repeats? How would you go about discovering if this transposase is flanked or not by inverted/direct repeats?
 
    <details open>

    <summary>See more</summary>
 
    - First, lets grab the first 10 and last 10 nucleotides to search for direct repeats. We can do this using the "Select sequence region" button (<img src="./images/UGENE/UGENE_select_button.png" height="17" title="Select sequence region">) 🖱️, setting the ranges `1..10` and `1003..1012` and then clicking <img src="./images/UGENE/UGENE_go_button.png" height="17"> 🖱️. Once region is selected hit <kbd>Ctrl + C</kbd> to copy.

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
    
    - To create the annotations, manually select the direct repeats at the start () and end () of the sequence. For each, click (<kbd>Ctrl + N</kbd>) 🖱️. This will open the "Create Annotation" window. We will select `repeat_region` from the "Annotation type" menu, and write `repeat_region` in both "Group name" and "Annotation name" fields. Now let's click <img src="./images/UGENE/UGENE_create_button.png" height="17"> 🖱️.
    
      ![](./images/UGENE/3.21_UGENE_annot_ISCca4_DR_create.png)
      <br/><br/>
 
    - As with `CDS`, we need to add some qualifiers. This is achieved by selecting the `repeat_region` and then clicking <kbd>Insert</kbd>. You will get an "Add new qualifier" pop-up window to type in: 
      - Name: `rpt_type`, Value: `DIRECT`.
    
        ![](./images/UGENE/3.22_UGENE_annot_ISCca4_DR_rptType_create.png)
        <br/><br/>

      - Name: `note`, Value: `target site duplication generated by insertion of ISCca10`.

        ![](./images/UGENE/3.23_UGENE_annot_ISCca4_DR_note_create.png)
        <br/><br/>

    </details>
    <br/><br/>


#### References
Siguier P, Perochon J, Lestrade L, Mahillon J, Chandler M. ISfinder: the reference centre for bacterial insertion sequences. *Nucleic acids research* 2006;34:D32-6. [https://doi.org/10.1093/nar/gkj014](https://doi.org/10.1093/nar/gkj014).

Siguier P, Varani A, Perochon J, Chandler M. *Exploring bacterial insertion sequences with ISfinder: objectives, uses, and future developments*. In: Bigot Y (editor). *Mobile Genetic Elements: Protocols and Genomic Applications*. Totowa, NJ: Humana Press. pp. 91–103. [https://doi.org/10.1007/978-1-61779-603-6_5](https://doi.org/10.1007/978-1-61779-603-6_5).
<br/>

<p align="right">
    <kbd> <br> <a href="./Part_3.md"><big><b>Next: Part 3</b></big></a> <br> </kbd>
</p>
