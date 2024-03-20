## Geneious
We will be using Geneious to visualize our mitogenomes. Create a new folder called "Genome_skimming_2024" inside the folder named "Local" in Geneious. Within this folder, create a separate folder for each of your samples.

### Read Assembly to Mitogenome

Import your getorganelle contigs into their respective folders. You can do this either by dropping-and-dragging the file, or import through the dropdown menus: File>Import>Files... Import your bowtie2_getorganelle BAM file into the same folder. When you import the .BAM file, it should create a new contig file that displays read sequeces assembled to your mitogenome sequence. <img src="https://github.com/SmithsonianWorkshops/Genome_Skimming_Workshop_LAB_2024/blob/main/images/Map_Reads_To_Assembly.png" alt="map_reads_to_reference_Geneious" width=600px>. When you have finished exploring your mapped reads (before importing your annotatons) delete your GetOrganelle contig. Conversely, import your annotation files first (do "Mitogenome annotation", below, first)

### Mitogenome annotation
Import your MitoFinder_getorganelle .gff file into the sample folder, either via drop-and-drag or through the dropdown menus. Highlight the just-imported file. Through the dropdown menu (File>Import>Files), import the Mitos_getorganelle .gff file. It will ask you if you want to attach this file to the current file. Yes, you do. You should now have a mitogenome sequence and two annotations, one from Mitofinder and one from MITOS, saved onto different tracks attached to the mitogenome. These are your annotated mitogenomes. We will examine the annotations further in Geneious.

