# Parallel Corpus

This dataset contains the parallel corpus generated from the alignment of DCS and Sanskrit Heritage Segmenter. It has the following:

1. parallel\_data\_iast.tsv -> list of entries from DCS and their corresponding ground truth segmentations. It is in the format (sentence_id, sentence, segmentation)

2. dcs\_sh\_graphml.zip -> contains the graphml files for all the sentences. These are generated from the Heritage Segmenter and aligned with the DCS corpus. Please check this link to download the same: [dcs_sh_alignment](https://drive.google.com/drive/folders/1r4IgONLVboMvzh9B5ZJKnrW0lqW25J53?usp=sharing)

3. dcs\_sh\_json.zip -> contains the analysis of the sentences in the json format. It is available here: [dcs_sh_alignment](https://drive.google.com/drive/folders/1r4IgONLVboMvzh9B5ZJKnrW0lqW25J53?usp=sharing)

## Graphml files

1. The analysis from Sanskrit Heritage Segmenter is scrapped and converted into a graph format which is stored in a .graphml file. This can be accessed using standard graph processing libraries like networkx.

2. Each of the graphml files stores the Segmenter's analysis of a sentence in the form of a graph, where the nodes represent segments and edge values represent whether the participating nodes can co-occur in a solution
    1. Edge-value "1" indicates that the two nodes cannot co-occur in a solution
    2. Edge-value "2" indicates that the two nodes can co-occur in a solution
    3. Edge-value "3" indicates that the two nodes can co-occur in a solution, and this edge is a part of the ground truth segmentation solution

3. Each of the nodes has the following attributes:
    1. id -> node id
    2. level -> the Heritage Segmenter displays the segments in the form of rows (levels) where each row has a unique possible segments for the same sandhied chunk
    3. color_class -> each phase (pos) is associated with a specific color
    4. position -> character position inside a chunk
    5. chunk_no -> the joint sentence is split into chunks and segmentation is done for each chunk separately
    6. word -> final word form
    7. stem -> derived stem
    8. base\_stem -> base stem
    9. cng -> value corresponding to the inflectional morph analysis
    10. base\_cng -> value corresponding to the derivational morph analysis
    11. morph -> inflectional morphological analysis
    12. base\_morph -> derivational morphological analysis
    13. sense -> sense of the stem
    14. base\_sense -> sense of the base\_stem
    15. pre\_verb -> pre\_verb in the inflected form
    16. base\_pre\_verb -> pre\_verb of the base form
    17. colspan -> character span of word
    18. wordlength -> length the word form
    19. aux_inf -> auxiliary information
    20. cha_pos -> overall character position in the input string
    
4. There are 130,271 graphml files named corresponding to the DCS sentence IDs present in the parallel\_data\_iast.tsv

## JSON files

1. There are 130,271 json files named corresponding to the DCS sentence IDs present in the parallel\_data\_iast.tsv

2. Each json file has the following:
    1. sent\_id -> sentence id corresponding to the DCS sentence
    2. sentence -> joint sentence<br>
    The following are in the format of a list of lists, representing the sequence of the segments. The outer list indicating the chunks. The inner list within each chunk indicates the individual segments.
    3. cng -> values corresponding to the inflectional morph analyses
    4. base\_cng -> values corresponding to the derivational morph analyses
    5. sense -> senses of the stems
    6. base\_sense -> senses of the base\_stems
    7. morph -> inflectional morphological analyses
    8. base\_morph -> derivational morphological analyses
    9. stem -> derived stems
    10. base\_stem -> base stems
    11. word -> word forms
    12. pre\_verb -> pre\_verbs of both the stems
    13. graphml\_node\_ids -> the node ids corresponding to the ids in the graphml graph
