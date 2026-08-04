---
jupyter:
  jupytext:
    formats: ipynb,md
    text_representation:
      extension: .md
      format_name: markdown
      format_version: '1.3'
      jupytext_version: 1.19.5
  kernelspec:
    display_name: Python 3 (ipykernel)
    language: python
    name: python3
---

<!-- #region editable=true slideshow={"slide_type": ""} tags=["title"] -->
# Local and global geographies. Shell companies in Luxembourg (1929-2016)
<!-- #endregion -->

<!-- #region editable=true slideshow={"slide_type": ""} tags=["contributor"] -->
### Benoît  Majerus [![orcid](https://orcid.org/sites/default/files/images/orcid_16x16.png)](https://orcid.org/0000-0003-4869-2061) 
Centre for Contemporary and Digital History, University of Luxembourg
<!-- #endregion -->

<!-- #region editable=true slideshow={"slide_type": ""} tags=["contributor"] -->
### Lars Wieneke [![orcid](https://orcid.org/sites/default/files/images/orcid_16x16.png)](https://orcid.org/0000-0001-6248-8644) 
Centre for Contemporary and Digital History, University of Luxembourg
<!-- #endregion -->

<!-- #region editable=true slideshow={"slide_type": ""} tags=["contributor"] -->
### Demival  Vasques Filho [![orcid](https://orcid.org/sites/default/files/images/orcid_16x16.png)](https://orcid.org/0000-0002-4552-0427) 
Centre for Contemporary and Digital History, University of Luxembourg
<!-- #endregion -->

<!-- #region tags=["copyright"] -->
[![cc-by-nc-nd](https://licensebuttons.net/l/by-nc-nd/4.0/88x31.png)](https://creativecommons.org/licenses/by-nc-nd/4.0/) 
©<AUTHOR or ORGANIZATION / FUNDER>. Published by De Gruyter in cooperation with the University of Luxembourg Centre for Contemporary and Digital History. This is an Open Access article distributed under the terms of the [Creative Commons Attribution License CC-BY-NC-ND](https://creativecommons.org/licenses/by-nc-nd/4.0/)

<!-- #endregion -->

```python editable=true slideshow={"slide_type": ""} tags=["cover"]
from IPython.display import Image, display

display(Image(("./media/cover-letterbox.jpg")))
```

<!-- #region editable=true slideshow={"slide_type": ""} tags=["keywords"] -->
Shell companies, Offshore finance, Luxembourg, Domiciliation, Tax havens
<!-- #endregion -->

<!-- #region editable=true slideshow={"slide_type": ""} tags=["abstract"] -->
Shell companies are a cornerstone of 20th-century global capitalism, yet there has been little research into their historical trajectories and infrastructural roles. Luxembourg, a pivotal offshore financial centre since the 1920s, exemplifies how these entities bridge local geographies and transnational tax networks, but systematic analyses of their evolution are lacking. Here, we combine digital methods with archival research to reconstruct the development of Luxembourg’s shell company sector from 1929 to 2016, leveraging public company registers to map their spatial and temporal dynamics.

We reveal two key patterns: locally, shell companies transitioned from hyper-concentration around Boulevard Royal in the 1930s—where banks and notaries dominated domiciliation—to a decentralised model by the 2010s, expanding to districts like Kirchberg as specialised fiduciaries displaced traditional actors. Globally, Luxembourg’s networks shifted from early reliance on Switzerland to partnerships with emerging hubs like the British Virgin Islands (1980s) and Ireland (1990s), with case studies of Panama and Niue illustrating adaptive integration into evolving tax chains. Crucially, we identify “hidden helpers”—notaries, lawyers, and fiduciaries—whose intermediary roles sustained these networks despite regulatory changes.

Methodologically, we took an innovative approach by applying computational techniques (GIS mapping, network analysis, and NLP-driven entity extraction) to fragmented, multilingual registers, enabling large-scale analysis of approximately 2.9 million business entries while addressing biases in digitised historical data. Our findings challenge narratives centred solely on banks, demonstrating how shell companies, as infrastructural tools, reflect Luxembourg’s interplay of sovereignty, European integration, and global finance.

This study advances debates on offshore finance by unifying local and global scales of analysis, revealing the resilience of shell company infrastructures amid regulatory pressures like the EU’s “Unshell” Directive. It also underscores digital history’s potential—and limitations—for critiquing financial opacity, offering a model for interdisciplinary research at the nexus of economic history, geography, and data science.
<!-- #endregion -->

<!-- #region editable=true slideshow={"slide_type": ""} -->
## Introduction
<!-- #endregion -->

<!-- #region citation-manager={"citations": {"2v9np": [{"id": "6915743/N3XT428Q", "source": "zotero"}], "ppj6n": [{"id": "6915743/PCWSS248", "source": "zotero"}], "zrsgk": [{"id": "6915743/N3XT428Q", "source": "zotero"}]}} editable=true slideshow={"slide_type": ""} -->
In December 2021, the European Commission presented the “Unshell” Directive, designed to combat the misuse of shell entities for tax avoidance within the European Union <cite id="2v9np"><a href="#zotero%7C6915743%2FN3XT428Q">(Sinnig &#38; Zetzsche, 2023)</a></cite>. This measure was introduced in the context of significant strain on public finances during the COVID-19 pandemic, which saw a substantial increase in public deficits across most European states. However, the directive is part of a broader long-term effort in global tax governance to curb various forms of tax evasion. A global system of tax governance has been in the making since at least the interwar period <cite id="ppj6n"><a href="#zotero%7C6915743%2FPCWSS248">(Farquet, 2010)</a></cite>, but moments of intense development were followed by long periods of inactivity. The Unshell Directive is part of a longer sequence that can be traced back to two events: the financial crisis that hit the world starting in 2007, and the scandalisation of certain practices by consortia of journalists, reflected by stories such as the Panama Papers, LuxLeaks and Cyprus Confidential. The OECD and G20 committed to creating an international framework to combat tax avoidance by multinational enterprises, starting in 2013 with the adoption of the Base Erosion and Profit Shifting (BEPS) Action Plan. Since 2016, the European Union has launched several Anti-Tax Avoidance Directives (ATADs). The Unshell Directive was proposed as “ATAD 3” <cite id="zrsgk"><a href="#zotero%7C6915743%2FN3XT428Q">(Sinnig &#38; Zetzsche, 2023)</a></cite>. At the time of publishing this article, the Unshell Directive is still working its way through the labyrinthine process of the infamous EU trilogue.
<!-- #endregion -->

<!-- #region citation-manager={"citations": {"guh8f": [{"id": "6915743/JVF2GSFJ", "source": "zotero"}]}} editable=true slideshow={"slide_type": ""} -->
The subsequent transposition of the directive into each Member State will reveal its true implications for tax chains, with Luxembourg sometimes taking a long time to transpose directives that seem unfavourable to its financial centre <cite id="guh8f"><a href="#zotero%7C6915743%2FJVF2GSFJ">(Bourbaki, 2016)</a></cite>. Regardless of the fate of the Unshell Directive, it has shone a light on shell companies as a tool for tax planning and beneficial ownership avoidance.
<!-- #endregion -->

<!-- #region citation-manager={"citations": {"33wsg": [{"id": "6915743/9ASG5329", "source": "zotero"}], "58pt9": [{"id": "6915743/MH4PGKJU", "source": "zotero"}], "8uxyo": [{"id": "6915743/9UCXNVVN", "source": "zotero"}], "9ow88": [{"id": "6915743/DHFSHPT9", "source": "zotero"}], "9sdy9": [{"id": "6915743/GJCWQT36", "source": "zotero"}], "h2p1t": [{"id": "6915743/P5W589ED", "source": "zotero"}], "lhrbc": [{"id": "6915743/VU5ZX59D", "source": "zotero"}]}} editable=true slideshow={"slide_type": ""} -->
Shell companies are difficult to define: most authors agree that a common trait is the absence of any economic substance and that they are an essential part of several tax havens <cite id="9sdy9"><a href="#zotero%7C6915743%2FGJCWQT36">(Beckett, 2023)</a></cite>. Switzerland, Luxembourg and the British Virgin Islands all introduced legal structuring of companies that permitted tax reduction and anonymisation, the first two through the holding regime that became a “refuge for capital flight” <cite id="58pt9"><a href="#zotero%7C6915743%2FMH4PGKJU">(Paquier, 2001)</a></cite>, 179) in the interwar period, and the BVI through the International Business Company Act in the 1990s <cite id="8uxyo"><a href="#zotero%7C6915743%2F9UCXNVVN">(<i>Maurer - 2000 - Recharting the Caribbean Land, Law, and Citizensh.Pdf</i>, n.d.)</a></cite>. But they had not previously attracted much attention, one exception being the recent tax loopholes revealed in the US state of Delaware <cite id="h2p1t"><a href="#zotero%7C6915743%2FP5W589ED">(Weitzman, 2022)</a></cite>. Shell companies are nonetheless an essential infrastructure in global tax chains: most offshore centres offer this legal construct, including Luxembourg. Although Luxembourg was not among the first generation of tax havens <cite id="lhrbc"><a href="#zotero%7C6915743%2FVU5ZX59D">(Guex, 2022)</a></cite><cite id="9ow88"><a href="#zotero%7C6915743%2FDHFSHPT9">(Watteyne, 2023)</a></cite>, by the late 1920s it had adopted a legal structure—the holding company—that positioned it in the market for tax engineering and the anonymisation of actual beneficiaries <cite id="33wsg"><a href="#zotero%7C6915743%2F9ASG5329">(Calabrese &#38; Majerus, 2024)</a></cite>.

<!-- #endregion -->

<!-- #region citation-manager={"citations": {"5p99b": [{"id": "6915743/MJWQASUP", "source": "zotero"}], "pkwxq": [{"id": "6915743/E2IA8V5V", "source": "zotero"}], "s8202": [{"id": "6915743/NHPDT9TF", "source": "zotero"}], "v2t82": [{"id": "6915743/9RDE745W", "source": "zotero"}], "vp5f7": [{"id": "6915743/PQHTQ4XU", "source": "zotero"}]}} editable=true slideshow={"slide_type": ""} -->
Based on publicly available company registers, this article maps shell companies as an essential infrastructure within the Luxembourg offshore financial centre by analysing how they were positioned in the local geography of Luxembourg City and how they linked to other offshore centres in larger global tax chains. Geographers have been studying the geography of the Luxembourg financial centre for some time now, focusing on its local dynamics as well as its role in global financial geography <cite id="5p99b"><a href="#zotero%7C6915743%2FMJWQASUP">(Walther et al., 2011)</a></cite><cite id="vp5f7"><a href="#zotero%7C6915743%2FPQHTQ4XU">(Dörry, 2016)</a></cite><cite id="s8202"><a href="#zotero%7C6915743%2FNHPDT9TF">(Hesse &#38; Wong, 2019)</a></cite>, although there has been little emphasis on the historical dimension of this process. Historians have scarcely explored this topic, preferring to concentrate on banks <cite id="v2t82"><a href="#zotero%7C6915743%2F9RDE745W">(Pauly, 2018)</a></cite><cite id="pkwxq"><a href="#zotero%7C6915743%2FE2IA8V5V">(Duval et al., 2023)</a></cite>. While banks are certainly significant actors, they are not the only financial service providers. The establishment of shell companies, whose headquarters are often located in the offices of service providers, allows for a parallel or complementary geography of the financial sector.
<!-- #endregion -->

<!-- #region editable=true slideshow={"slide_type": ""} -->
# Sources

<!-- #endregion -->

<!-- #region editable=true slideshow={"slide_type": ""} -->
In the midst of World War I, Luxembourg reformed its corporate regulation with the Act of 10 August 1915 (Loi du 10 août 1915 concernant les sociétés commerciales). This law required all companies established in Luxembourg to publish certain details. This information was originally published as an appendix to the Mémorial, the Official Journal of the Grand Duchy of Luxembourg, but from 1960 onwards it was given a separate publication, Mémorial C (as laid down in the Règlement grand-ducal du 9 janvier 1961 relatif aux trois recueils du Mémorial, n.d.). 
<!-- #endregion -->

<!-- #region editable=true slideshow={"slide_type": ""} tags=["hermeneutics"] -->
Unfortunately the corpus does not exist in a digitised, coherent and semi-structured format. The years 1929-1960 were scanned at the Luxembourg Centre for Contemporary and Digital History (C2DH) on a Treventus ScanRobot 2.0 MDS book scanner (400 dpi in tif format), and optical character recognition (OCR) was used to extract text from the scanned documents. However, during the process we encountered several challenges that significantly impacted the accuracy and reliability of the extracted text.
<!-- #endregion -->

<!-- #region editable=true slideshow={"slide_type": ""} tags=["hermeneutics"] -->
One of the primary issues was related to the layout of the scanned documents. The pages contained white margins that acted as long 2D separators, inadvertently segmenting business descriptions. This disrupted the logical flow of the text and led to incorrect parsing. Additionally, some pages were distorted and skewed, tilting either left or right, which further complicated text extraction and alignment (Fig. 1). These challenges underscore the complexities associated with OCR processing when dealing with inconsistent document layouts and distortions. To deal with this problem programmatically, it was necessary to implement advanced preprocessing techniques such as margin removal, deskewing algorithms and language-specific OCR models. These enhancements help mitigate errors and ensure more reliable text extraction in the OCR application. However, since the number of mentioned businesses in the documents for this period was not considerable, and the above-mentioned methods require significant time and effort to implement, we decided to process this time period manually.
<!-- #endregion -->

```python editable=true slideshow={"slide_type": ""} tags=["figure-challenge-*"]
from IPython.display import Image 
metadata={
    "jdh": {
        "module": "object",
        "object": {
            "type":"image",
            "source": [
                "Fig. 1. Distorted and skewed scanned pages, tilting either left or right."
            ]
        }
    }
}
display(Image("./media/source-challenge.png"), metadata=metadata)
```

<!-- #region editable=true slideshow={"slide_type": ""} tags=["hermeneutics"] -->
Moving forward, the years 1961-1995 were digitised by the National Library of Luxembourg (BNL). Thanks to an agreement with the BNL, our research project was given access to these files, which are publicly available on e-luxemburgensia but with major restrictions, such as lacking indexation or search tool, only available for the titles of the articles. For the last remaining decades (1996-2016), we downloaded the PDF files from legilux.public.lu, as the Luxembourgish administration refused to give us access to the structured data they possess for the years 1996-2016. Thus, we had only access to "unstructured" pdfs.
<!-- #endregion -->

<!-- #region editable=true slideshow={"slide_type": ""} tags=["hermeneutics"] -->
Although these scanned documents were of relatively high quality, challenges remained in extracting text using OCR. In particular, the multilingual nature of the documents—written in French, German and Luxembourgish—introduced additional complications. Accented characters such as é, ä, ü and ö were frequently misrecognised, leading to character-level errors. Punctuation marks also caused ambiguities: for example, a full stop following a capital letter was sometimes misread (e.g. “I.” was read as “L” and ”O.” was incorrectly identified as “Q”).
<!-- #endregion -->

<!-- #region editable=true slideshow={"slide_type": ""} tags=["hermeneutics"] -->
These challenges affected the quality of the information extracted from the scanned documents. To improve accuracy, we employed generative AI (large language models—LLMs), combined with human review, as part of a post-cleaning and information enhancement process to mitigate the impact of these issues on the extracted business descriptions. It is worth noting that, despite these refinements, the dataset contains approximately 3 million business descriptions from 1961 to 2016. Assuming an average of 30 seconds per post-cleaning task, it would take roughly three years to process the entire dataset. Therefore, some degree of inaccuracy remains and is expected to be gradually corrected in the coming years.
<!-- #endregion -->

<!-- #region editable=true slideshow={"slide_type": ""} tags=["hermeneutics"] -->
In summary, the register of companies in Luxembourg is publicly available for the years 1940 to 1959 on paper in some libraries in Luxembourg, and for the years 1929 to 1939 and 1961 to 2016 on the web. The publication policies are different, however: paradoxically the BNL imposes stricter protections on the older data (1929-1939, 1961-1996) than the Central Legislative Service in the Ministry of State, responsible for the website legilux.public.lu, which publishes records for the years 1996-2016.
<!-- #endregion -->

<!-- #region citation-manager={"citations": {"8osce": [{"id": "6915743/9NP9K8Z4", "source": "zotero"}]}} editable=true slideshow={"slide_type": ""} -->
The register of companies does not fall under the restrictions of the Luxembourg Archives Act as it is publicly available from the day it is published. But as data is collected, analysed, stored and processed, the General Data Protection Regulation (GDPR), in force in the European Union since 2018, applies. Although the GDPR explicitly provides for exceptions for research, the wording remains somewhat vague. While there is now a growing body of case law concerning certain data collections and publications—especially for services such as online tracking (offered by Google, for example) or for journalism <cite id="8osce"><a href="#zotero%7C6915743%2F9NP9K8Z4">(Bitiukova, 2023)</a></cite>—, historians have done little to standardise their practices, apart from complying with obligations towards data holders.
<!-- #endregion -->

<!-- #region citation-manager={"citations": {"1wwnm": [{"id": "6915743/BM2KP27N", "source": "zotero"}], "9i7ou": [{"id": "6915743/ZIHW85VR", "source": "zotero"}], "um1qn": [{"id": "6915743/H9ZKDADQ", "source": "zotero"}]}} editable=true slideshow={"slide_type": ""} -->
Some of the solutions proposed in the literature could not be applied for this project. Obtaining authorisation from all individuals whose names are mentioned (around 350,000 people in our database) would require a disproportionate effort. Pseudonymisation or anonymisation during both data collection and publication is contrary to the goal of the research, which specifically aims to identify the manufacturing chains of shell companies and to historicise the actors and uncover the societal networks within which they operated <cite id="um1qn"><a href="#zotero%7C6915743%2FH9ZKDADQ">(Luyten, 2022)</a></cite><cite id="1wwnm"><a href="#zotero%7C6915743%2FBM2KP27N">(Friedewald, forthcoming)</a></cite>. If necessary for the historical argument, we will therefore publish the names of financial service providers such as notaries, lawyers and bankers. While the “indeterminate legal concepts” and “large scopes of interpretation” <cite id="9i7ou"><a href="#zotero%7C6915743%2FZIHW85VR">(Jahnel, 2023)</a></cite> of the GDPR allow such a practice, we nevertheless inserted a “Your section” on the project web page allowing people to access and correct information we collected.
<!-- #endregion -->

<!-- #region editable=true slideshow={"slide_type": ""} -->
# Generating data: the ETL workflow for historical records
<!-- #endregion -->

<!-- #region editable=true slideshow={"slide_type": ""} tags=["hermeneutics"] -->
In this study, we process unstructured data in PDF format (scanned documents) through an ETL (extract, transform, load) workflow (Fig. 2). The process involves extracting data using 2D line detection, transforming it into a structured text format with the help of LLMs, and loading it into a relational database specifically designed for these data. In the following subsections, we present each step of this workflow in more detail.
<!-- #endregion -->

```python editable=true slideshow={"slide_type": ""} tags=["figure-schematic-*"]
from IPython.display import Image 
metadata={
    "jdh": {
        "module": "object",
        "object": {
            "type":"image",
            "source": [
                "Fig. 2. Schematic drawing of a standard ETL (extract, transform, load) workflow used to convert unstructured data into structured data and make it available in a dedicated database. In this research, “extract” involved reading scanned documents and capturing business descriptions for each company; “transform” involved applying named entity recognition (NER); and “load” involved saving the structured NER output and business descriptions into a database."
            ]
        }
    }
}
display(Image("./media/etl-schematic.png"), metadata=metadata)
```

<!-- #region editable=true slideshow={"slide_type": ""} -->
## Extract
<!-- #endregion -->

```python editable=true slideshow={"slide_type": ""}
!python.exe -m pip install --upgrade pip
!pip install pytesseract
!pip install opencv-python
!pip install pdfplumber
!pip install peft
!pip install trl
!pip install tensorboard
!pip install tensorboardX
```

<!-- #region citation-manager={"citations": {"6b0iz": [{"id": "6915743/E738G59W", "source": "zotero"}], "s5wus": [{"id": "6915743/IBNZ2AD7", "source": "zotero"}]}} editable=true slideshow={"slide_type": ""} tags=["hermeneutics"] -->
In the extract step of the ETL workflow, unstructured PDF documents are processed to extract text data using a combination of optical character recognition (OCR) and advanced image preprocessing techniques. Each page of the PDF is first converted into an image using the PDFPlumber library <cite id="s5wus"><a href="#zotero%7C6915743%2FIBNZ2AD7">(Singer-Vine &#38; Jain, 2025)</a></cite>. These images are then preprocessed by converting them to greyscale and applying binary thresholding to enhance text visibility. Line detection uses morphological operations to identify horizontal structures, which segment the image into manageable regions. The segmented areas are processed using Tesseract OCR <cite id="6b0iz"><a href="#zotero%7C6915743%2FE738G59W">(Hoffstaetter, 2025)</a></cite>, configured with multilingual support for languages such as French, German, Luxembourgish and English, to obtain high-quality textual data. The extracted content is subsequently refined and organised into coherent blocks based on line and paragraph alignment to improve readability and accuracy. Finally, the structured text is aggregated and saved to a text file, preparing it for the subsequent transformation and loading phases. An explanation of the parameters and components used in the extraction process is outlined below. The script begins by importing essential libraries for file handling (os), image processing (cv2, PIL), optical character recognition (pytesseract), PDF parsing (PDFPlumber) and data manipulation (Pandas, NumPy). The Tesseract OCR engine is configured by specifying its executable path, and multilingual support is verified via a subprocess to list installed languages.
<!-- #endregion -->

<!-- #region editable=true slideshow={"slide_type": ""} tags=["hermeneutics"] -->
Input and output paths are defined to manage the location of PDF files and the resulting extracted text. The core extract_text function performs preprocessing steps such as greyscale conversion and binary thresholding to improve OCR accuracy. Tesseract is then used to extract text in multiple languages (French, German, Luxembourgish and English), organising content into structured text blocks with attention to alignment and spacing.
<!-- #endregion -->

<!-- #region editable=true slideshow={"slide_type": ""} tags=["hermeneutics"] -->
The main processing loop iterates through each PDF in the input directory, converting pages into images and applying morphological operations to detect horizontal lines. These lines are used to segment the page into distinct regions, from which text is extracted and formatted. The refined text from all pages is aggregated and saved as a single structured text file. For validation purposes, Matplotlib is used to visualise both the original pages and cropped sections during processing. The final output includes the structured text and a log of the processing status for each file.
<!-- #endregion -->

```python editable=true slideshow={"slide_type": ""}
import os
import cv2
import pytesseract
import pdfplumber
from PIL import Image
import numpy as np
import matplotlib.pyplot as plt  # For displaying images
from pytesseract import Output
import pandas as pd
import subprocess

# Configure Tesseract executable path for Windows
pytesseract.pytesseract.tesseract_cmd = r'C:\Program Files\Tesseract-OCR\tesseract.exe'

# List installed languages to verify Tesseract setup
result = subprocess.run([pytesseract.pytesseract.tesseract_cmd, '--list-langs'], stdout=subprocess.PIPE, text=True)
print("Installed Tesseract Languages:\n", result.stdout)

# Path where processed files will be saved
pathW = "\\JDH_PAPER\\"  # Adjust path to your environment

def extract_text(image):
    """
    Extract text from an image using Tesseract OCR.

    Args:
        image (numpy.ndarray): Input image from which text will be extracted.

    Returns:
        str: Extracted text.
    """
    try:
        # Convert the image to grayscale
        gray = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)
    except Exception as e:
        gray = image
        print(f"Error during grayscale conversion: {e}")
    
    try:
        # Apply binary thresholding to enhance text contrast
        thresh = cv2.threshold(gray, 0, 255, cv2.THRESH_BINARY_INV + cv2.THRESH_OTSU)[1]
    except Exception as e:
        print(f"Error during thresholding: {e}")
        thresh = image

    # Configure Tesseract for multilingual OCR
    custom_config = r'-c preserve_interword_spaces=1 --oem 1 --psm 6 -l fra+deu+ltz+eng'
    
    # Extract OCR data from image
    d = pytesseract.image_to_data(thresh, config=custom_config, output_type=Output.DICT)
    df = pd.DataFrame(d)
    df1 = df[(df.conf != '-1') & (df.text != ' ') & (df.text != '')]

    # Sort text blocks vertically
    sorted_blocks = df1.groupby('block_num').first().sort_values('top').index.tolist()
    text = ''
    for block in sorted_blocks:
        curr = df1[df1['block_num'] == block]
        sel = curr[curr.text.str.len() > 5]
        char_w = (sel.width / sel.text.str.len()).mean()
        prev_par, prev_line, prev_left = 0, 0, 0
        for ix, ln in curr.iterrows():
            # Add new line when switching paragraphs or lines
            if prev_par != ln['par_num']:
                text += '\n'
                prev_par = ln['par_num']
                prev_line = ln['line_num']
                prev_left = 0
            elif prev_line != ln['line_num']:
                text += '\n'
                prev_line = ln['line_num']
                prev_left = 0

            # Calculate space adjustments for alignment
            added = 0
            if ln['left'] / char_w > prev_left + 1:
                added = int((ln['left']) / char_w) - prev_left
                text += ' ' * added
            text += ln['text'] + ' '
            prev_left += len(ln['text']) + added + 1
        text += " \n"
    return text

# Process each year within a specific range
for year in range(1961, 1962):
    path = "\\JDH_PAPER\\"  # Adjust this path accordingly
    List = os.listdir(path)
    previous_end_crop = ""  # Stores the last crop of a page to combine with the next page if necessary
    
    for each in List:
        if each.endswith(".pdf"):
            print(f"Processing file: {each}")
            pdf_file = os.path.join(path, each)
            outputFilesPath = os.path.join(pathW, each.replace(".pdf", ".txt"))
            my_pdf = pdfplumber.open(pdf_file)
            
            y_all = {i: [] for i in range(len(my_pdf.pages))}
            All_Text = ""
            All_Text += "========================================================== \n"
            All_Text += f"\n +++++++++++++++++ \n File name: {each} Page Number: {1}\n +++++++++++++++++ \n"
            
            for i in range(len(my_pdf.pages)):
                # Convert each page to an image
                im = my_pdf.pages[i].to_image(resolution=420)
                print(f"Processing page {i + 1}")
                im.save("\\JDH_PAPER\\temporary.png", "PNG")
                image = cv2.imread("\\JDH_PAPER\\temporary.png")

                # Display the original page
                plt.figure(figsize=(12, 10))
                plt.imshow(cv2.cvtColor(image, cv2.COLOR_BGR2RGB))
                plt.title(f"Original Page {i}")
                plt.axis('off')
                plt.show()

                # Preprocess for line detection
                gray = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)
                thresh = cv2.threshold(gray, 0, 255, cv2.THRESH_BINARY_INV + cv2.THRESH_OTSU)[1]
                kernel = cv2.getStructuringElement(cv2.MORPH_RECT, (2, 1))
                dilated = cv2.dilate(thresh, kernel, iterations=2)
                horizontal_kernel = cv2.getStructuringElement(cv2.MORPH_RECT, (320, 1))
                detected_lines = cv2.morphologyEx(dilated, cv2.MORPH_OPEN, horizontal_kernel, iterations=2)

                # Detect lines and extract their coordinates
                cnts = cv2.findContours(detected_lines, cv2.RETR_EXTERNAL, cv2.CHAIN_APPROX_SIMPLE)
                cnts = cnts[0] if len(cnts) == 2 else cnts[1]

                for c in cnts:
                    y = c[0][0][1]
                    if y > 0:
                        y_all[i].append(y)

                y_all[i] = sorted(list(set(y_all[i])))
                print("Detected line y-coordinates:", y_all[i])

                start = [0] + y_all[i] + [image.shape[0]]

                # Crop and process each region between detected lines
                for k in range(len(start) - 1):
                    cropImage = image[start[k]:start[k + 1], :]
                    plt.figure(figsize=(12, 10))
                    plt.imshow(cv2.cvtColor(cropImage, cv2.COLOR_BGR2RGB))
                    plt.title(f"Page {i} - Crop {k + 1}")
                    plt.axis('off')
                    plt.show()

                    text = extract_text(cropImage)
                    print("Extracted text:", text)

                    if k == len(start) - 2 and i != len(my_pdf.pages) - 1:
                        previous_end_crop = text
                    else:
                        All_Text += text
                        All_Text += "\n ========================================================== \n"
                        All_Text += f"\n +++++++++++++++++ \n File name: {each} Page Number: {i + 1}\n +++++++++++++++++ \n"
                
                if previous_end_crop:
                    All_Text += previous_end_crop
                    previous_end_crop = ""
            
            # Save extracted text to file
            with open(outputFilesPath, "w") as outputFiles:
                outputFiles.write(All_Text)
            print("Processing completed for:", each)

```

## Transform

<!-- #region editable=true slideshow={"slide_type": ""} tags=["hermeneutics"] -->
In the transform phase of the ETL workflow, raw extracted data is cleaned, structured and enriched to ensure it is in a usable format for analysis. For this paper, we used generative AI models, specifically large language models (LLMs), to transform unstructured text into well-structured and semantically enriched formats, enabling more accurate and meaningful insights.
<!-- #endregion -->

<!-- #region editable=true slideshow={"slide_type": ""} tags=["hermeneutics"] -->
Now we explain a code that outlines a workflow to process a text file, extract valid company names using regex cleaning and a generative AI model, and save the results to an output file. It begins by importing essential libraries: transformers for using pre-trained models like Mistral, torch for GPU and model operations, re for pattern matching, and gc for memory cleanup. Two text-cleaning functions handle noise removal: clean_start_of_text_number1 removes leading characters and numbers, while clean_start_of_text_number2 removes text before two-digit numbers, accounting for short and uppercase formats. The Mistral model (microsoft/Orca-2-7b) and tokeniser are initialised with support for GPU and Hugging Face tokens. The validate_company_name function extracts and validates concise company names from descriptions using a structured prompt. extract_company_names generates names based on this prompt, cleans the output, and filters irrelevant information, such as lines with “Siège social” or “Sitz” (meaning registered office). The main workflow reads the input file line by line, cleans the text, prepares prompts, extracts and validates names, and filters invalid results (e.g. returning “Wrong” for non-company content). Memory is optimised during GPU-intensive processing using torch.cuda.empty_cache and gc.collect. Finally, results are saved to extracted_company_names.txt, pairing extracted company names with their original input lines using a delimiter (&&&****&&&) for easy parsing and analysis.
<!-- #endregion -->

```python editable=true slideshow={"slide_type": ""}
from transformers import AutoTokenizer, AutoModelForCausalLM
import torch,gc
import re

def clean_start_of_text_number1(input_text):
    # Remove any punctuation from the first characters
    cleaned_text = re.sub(r'^[^a-zA-ZÀ-ÖØ-öø-ÿÄäÖöÜüßÇçÉéÈèÊêËëÀàÂâÎîÏïÔôÛûÙùŸÿÆæŒœ]*', '', input_text)

    # Check if there's a number at the start of the text and remove everything before and including it
    match = re.search(r'^\s*\d+', cleaned_text)
    if match:
        # Remove the leading number and any preceding characters
        cleaned_text = cleaned_text[match.end():].strip()
    else:
        # If no number at the start, re-clean remaining leading junk characters
        cleaned_text = re.sub(r'^[^\wÀ-ÖØ-öø-ÿÄäÖöÜüßÇçÉéÈèÊêËëÀàÂâÎîÏïÔôÛûÙùŸÿÆæŒœ]+', '', cleaned_text).strip()
    
    return cleaned_text

def clean_start_of_text_number2(input_text):
    # Find the first occurrence of a number with 2 or more digits and remove all text preceding it
    if len(input_text)<50:
        end1=len(input_text)
    else:
        end1 =35
        if input_text[:end1].isupper()==True:
            end1=0
    match = re.search(r'\b\d{2,}', input_text[:end1])
    if match:
        # Remove everything before and including the first occurrence of the number
        cleaned_text = input_text[match.end():].strip()
    else:
        # If no number with 2 or more digits is found, return the original input
        cleaned_text = input_text.strip()
    
    return cleaned_text
    
# Initialize the Mistral model and tokenizer
model_name = "microsoft/Orca-2-7b"#"Open-Orca/Mistral-7B-OpenOrca"
# model_name = "mistralai/Mistral-7B-Instruct-v0.2"

device = "cuda" if torch.cuda.is_available() else "cpu"

print("Device:", device)

tokenizer = AutoTokenizer.from_pretrained(model_name, use_auth_token='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')
model = AutoModelForCausalLM.from_pretrained(model_name, use_auth_token='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').to(device)

def validate_company_name(company_description, suggested_company_name, model, tokenizer):
    """
    Validates and extracts the correct company name based on the provided description and suggested name.

    Args:
        company_description (str): The company description containing possible company names.
        suggested_company_name (str): The suggested full company name.
        model (AutoModelForCausalLM): Pretrained language model for causal generation.
        tokenizer (AutoTokenizer): Tokenizer corresponding to the pretrained model.

    Returns:
        str: Extracted concise company name.
    """
    prompt = (
        "You are tasked with validating and extracting the company name from a description. "
        "The company name may be written in full or as an abbreviation.\n\n"
        "Instructions:\n"
        "1. Identify the most concise version of the company name within the provided description.\n"
        "2. If an abbreviation or alternate form of the name is explicitly stated, extract that form.\n"
        "3. Return only the exact company name as it appears in the text, without any additional explanation or formatting.\n\n"
        "Example 1:\n"
        "Company Description: \"e OMNIUM INTERNATIONAL S.A.» en abréviation: « OMINTER ». Siège social: Luxembourg, 19, Boulevard Prince Henri.\"\n"
        "Suggested Company Name: \"OMNIUM INTERNATIONAL S.A.\"\n"
        "Output: \"OMINTER\"\n\n"
        "Example 2:\n"
        "Company Description: \"GLOBALTECH INNOVATIONS GmbH, also referred to as 'GLOBTECH'. Headquartered in Berlin.\"\n"
        "Suggested Company Name: \"GLOBALTECH INNOVATIONS GmbH\"\n"
        "Output: \"GLOBTECH\"\n\n"
        "Example 3:\n"
        "Company Description: \"Alpha Corp. Official Name: 'Alpha Corporation'.\"\n"
        "Suggested Company Name: \"Alpha Corp.\"\n"
        "Output: \"Alpha Corporation\"\n\n"
        "Company Description: ABC Société Anonyme. fabrique de cuivre, "
        "Suggested Company Name: \"ABC, Société Anonyme.  fabrique de cuivre,\"\n"
        "Output: \"ABC\"\n\n"
        "Now process the following:\n\n"
        f"Company Description: {company_description}\n"
        f"Suggested Company Name: {suggested_company_name}\n"
        f"Output:"
    )
    
    # Tokenize and generate response
    inputs = tokenizer(prompt, return_tensors="pt").to(model.device)
    with torch.no_grad():
        output = model.generate(**inputs, max_new_tokens=50, temperature=0.2, do_sample=False)
    
    # Decode the response and extract the result
    generated_text = tokenizer.decode(output[0], skip_special_tokens=True)
    extracted_name = generated_text.split("Output:")[-1].strip()
    return extracted_name

# Function to generate company name predictions
def extract_company_names(prompt, model, tokenizer):
    # Ensure inputs are on the same device as the model
    inputs = tokenizer(prompt, return_tensors="pt", truncation=True, max_length=200).to(device)
    outputs = model.generate(**inputs, max_new_tokens=30, eos_token_id=tokenizer.eos_token_id)
    output_text = tokenizer.decode(outputs[0], skip_special_tokens=True).replace("\n"," ").replace(prompt.replace("\n"," "),"").replace("\n","")
    if "company name:" in output_text:
        output_text=output_text.split("company name:")[1]
    if "Company name:" in output_text:
        output_text=output_text.split("Company name:")[1]
    if "company names:" in output_text:
        output_text=output_text.split("company names:")[1]
    if "Company names:" in output_text:
        output_text=output_text.split("Company names:")[1]
    if "Siège social" in output_text:
        output_text=output_text.split("Siège social")[0]
    if "Siege social" in output_text:
        output_text=output_text.split("Siege social")[0]
    if "Siége social" in output_text:
        output_text=output_text.split("Siége social")[0]
    if "Hauptsitz" in output_text:
        output_text=output_text.split("Hauptsitz")[0]
    if "Sitz" in output_text:
        output_text=output_text.split("Sitz")[0]
    if "sitz" in output_text:
        output_text=output_text.split("sitz")[0]
    if "S. à r." in output_text:
        output_text=output_text.split("S. à r.")[0]
    output_text = clean_start_of_text_number2(output_text)
    print("Output Text: ", output_text)
    return output_text


# Read the input file line by line
input_file = "/JDH_PAPER/1970-01-23_01_Single_Line.txt"  # Replace with your input text file
output_file = "/JDH_PAPER/extracted_company_names.txt"

with open(input_file, "r") as infile, open(output_file, "w") as outfile:
    for line in infile:
        line=line.strip().lstrip().rstrip()
        if len(line)>2:
            input_text=line.split('+++++++++++++++++')[-1].strip()
            if len(input_text)<130:
                end=len(input_text)
            else:
                end=130
            if "SOMMAIRE" in input_text[:20] or 'MEMORIAL Journal Officiel me Amtsblatt' in input_text[:end] or 'RECUEIL SPECIAL ue DES SOCIETES ET ASSOCIATIONS' in input_text[:end]:
                company_names="Wrong"
            else:
                input_text=input_text[:end]
                input_text=clean_start_of_text_number1(input_text)
                # input_text=clean_start_of_text(input_text)
    
                # Prepare the prompt for Mistral with clear instruction
                prompt = (
                    f"In the following text, company names are short and exact phrases from the input that appear at the start of the given text and are often found before terms like 'social:', 'RECTIFICATIF', 'Hauptsitz:' or 'Sitz:'. "
                    f"If the text is too short or it is not part of a company description, answer with 'Wrong'. "
                    f"It is possible for the given input text to begin with irrelevant characters. For example, in 'TT aaa ttt eeee aa oo 45 ALTA S. A. H. Siège social: Luxembourg,' the company name is 'ALTA S. A. H.' "
                    f"Extract the exact company names from the provided text without any additional explanation. The company name must be an exact substring of the input text. You must only provide the exact company name:\n\n"
                    f"{input_text.strip()}\n\n"
                    f"Company Names:"
                )
    
    
                print("prompt:",prompt)
                print("==========")
                generated_text = extract_company_names(prompt, model, tokenizer)
                generated_text= generated_text.rstrip().lstrip().strip()
                company_names = generated_text
                del generated_text
                torch.cuda.empty_cache()
                gc.collect()
                result = validate_company_name(input_text.strip(), company_names, model, tokenizer)
                company_names = result
                print("Final company_names:",company_names)
                print("***********************************")

                del result
                torch.cuda.empty_cache()
                gc.collect()
                # Filter valid company names
            
            # Write each company name to the output file
            outfile.write(company_names +" &&&****&&& "+line.replace("\n","")+ "\n")

print(f"Extraction completed. Company names are saved in extracted_company_names.txt.")

```

<!-- #region editable=true slideshow={"slide_type": ""} tags=["hermeneutics"] -->
Now we focus on another part of the implementation: extracting and validating individuals’ names from text using a combination of regular expressions and a generative AI model. This component is designed to handle multilingual and unstructured inputs effectively. The code begins by importing essential libraries—regex for advanced pattern matching with Unicode support, and transformers and torch to load the Mistral model (mistralai/Mistral-7B-Instruct- v0.3) and configure it for execution on GPU or CPU, with secure access via a Hugging Face authentication token.
<!-- #endregion -->

<!-- #region editable=true slideshow={"slide_type": ""} tags=["hermeneutics"] -->
The core logic includes a function, extract_sequences, which identifies personal name patterns such as initials, full names with titles, capitalised sequences and names with linguistic prefixes. These matches are consolidated into a filtered list of potential names. Additional functions like clean and clean_name ensure consistent formatting by removing excess whitespace, handling uppercase sequences, and accounting for cultural name structures.
<!-- #endregion -->

<!-- #region editable=true slideshow={"slide_type": ""} tags=["hermeneutics"] -->
To validate whether a string is likely a personal name, the is_person_name function constructs a structured prompt for the Mistral model and generates low-randomness responses for consistency. The file processing workflow reads input data line by line, splits each line using the delimiter &&&****&&&, and extracts the segment to be processed. Regex is first applied to extract name candidates, which are then validated by the AI model and formatted accordingly.
<!-- #endregion -->

<!-- #region editable=true slideshow={"slide_type": ""} tags=["hermeneutics"] -->
The final output includes the company name, validated personal names, and the original raw input, written to a new file with _people.txt appended to the filename. This approach enables scalable, efficient and language-agnostic name extraction while ensuring robustness against variations in formatting, abbreviations and irrelevant text.
<!-- #endregion -->

```python editable=true slideshow={"slide_type": ""}
import regex as re  # Importing regex module which supports Unicode property escapes

from transformers import AutoTokenizer, AutoModelForCausalLM
import torch
# Replace 'your_huggingface_token' with your actual Hugging Face access token
token = 'your_token'

# Load the model and tokenizer with the token for authentication
device = "cuda" if torch.cuda.is_available() else "cpu"

model_name = "mistralai/Mistral-7B-Instruct-v0.3"
tokenizer = AutoTokenizer.from_pretrained(model_name, token=token)
model = AutoModelForCausalLM.from_pretrained(model_name, token=token).to(device)

def extract_sequences(text):
    """
    Extract sequences of words that begin with a capital letter from the given text, including specific name patterns.

    Args:
    text (str): The input text to search within.

    Returns:
    tuple: Lists for "A. Dickes" style sequences, multi-word capitalized sequences,
           names with geographical or familial prefixes, sequences with titles, and general capitalized word sequences.
    """
    # Remove extra whitespace from the text
    text = re.sub(r'\s+', ' ', text)
    
    # Existing patterns
    pattern_abbr = r'\b[A-ZÄÖÜßÀÁÂÃÄÅÆÇÈÉÊËÌÍÎÏÐÑÒÓÔÕÖØÙÚÛÜÝŸČĆŠŽŒ]\.\s+[A-ZÄÖÜßÀÁÂÃÄÅÆÇÈÉÊËÌÍÎÏÐÑÒÓÔÕÖØÙÚÛÜÝŸČĆŠŽŒ][a-zäöüßàáâãäåæçèéêëìíîïðñòóôõöøùúûüýÿčćšžœ\'\-]*'
    
    pattern_full_name = r'\b(?:M\.|Mlle|Mme|Monsieur|Madame|Mademoiselle|Messieurs|Mesdames|Mesdemoiselles|Herr|Frau|Fräulein|Herren|Doktor|Dr\.|Här|Madamm|Härn|Sr\.|Sra\.|Srta\.|Don|Doña|Sres\.|Sras\.|Dres\.|Veuve|Witwe|Wittfra|Viuda\s+)?(?:[A-ZÄÖÜßÀÁÂÃÄÅÆÇÈÉÊËÌÍÎÏÐÑÒÓÔÕÖØÙÚÛÜÝŸČĆŠŽŒ][a-zäöüßàáâãäåæçèéêëìíîïðñòóôõöøùúûüýÿčćšžœ\'\-]*\s?)+(?:[A-ZÄÖÜßÀÁÂÃÄÅÆÇÈÉÊËÌÍÎÏÐÑÒÓÔÕÖØÙÚÛÜÝŸČĆŠŽŒ]\.\s)?[A-ZÄÖÜßÀÁÂÃÄÅÆÇÈÉÊËÌÍÎÏÐÑÒÓÔÕÖØÙÚÛÜÝŸČĆŠŽŒ][a-zäöüßàáâãäåæçèéêëìíîïðñòóôõöøùúûüýÿčćšžœ\'\-]*'
    
    pattern_multi_word = r'\b(?:[A-ZÄÖÜßÀÁÂÃÄÅÆÇÈÉÊËÌÍÎÏÐÑÒÓÔÕÖØÙÚÛÜÝŸČĆŠŽŒ][a-zäöüßàáâãäåæçèéêëìíîïðñòóôõöøùúûüýÿčćšžœ\'\-]*\s+){2,}'
    
    pattern_prefix = r'\b[A-ZÄÖÜßÀÁÂÃÄÅÆÇÈÉÊËÌÍÎÏÐÑÒÓÔÕÖØÙÚÛÜÝŸČĆŠŽŒ][a-zäöüßàáâãäåæçèéêëìíîïðñòóôõöøùúûüýÿčćšžœ\'\-]*\s+(?:de|van|von|de la|de los|de las)\s+[A-ZÄÖÜßÀÁÂÃÄÅÆÇÈÉÊËÌÍÎÏÐÑÒÓÔÕÖØÙÚÛÜÝŸČĆŠŽŒ][a-zäöüßàáâãäåæçèéêëìíîïðñòóôõöøùúûüýÿčćšžœ\'\-]*'
    
    pattern_general = r'\b(?:[A-ZÄÖÜßÀÁÂÃÄÅÆÇÈÉÊËÌÍÎÏÐÑÒÓÔÕÖØÙÚÛÜÝŸČĆŠŽŒ][a-zäöüßàáâãäåæçèéêëìíîïðñòóôõöøùúûüýÿčćšžœ\'\-]*\s*){2,}'
    
    # New pattern for names with initials and surname, such as "Monsieur H.J. Sulkers"
    pattern_initials_with_title = r'\b(?:M\.|Monsieur|Madame|Herr|Frau|Dr\.|Doktor|Här|Madamm)\s+[A-ZÄÖÜßÀÁÂÃÄÅÆÇÈÉÊËÌÍÎÏÐÑÒÓÔÕÖØÙÚÛÜÝŸČĆŠŽŒ](?:\.[A-ZÄÖÜßÀÁÂÃÄÅÆÇÈÉÊËÌÍÎÏÐÑÒÓÔÕÖØÙÚÛÜÝŸČĆŠŽŒ])?\.\s*[A-ZÄÖÜßÀÁÂÃÄÅÆÇÈÉÊËÌÍÎÏÐÑÒÓÔÕÖØÙÚÛÜÝŸČĆŠŽŒ][a-zäöüßàáâãäåæçèéêëìíîïðñòóôõöøùúûüýÿčćšžœ\'\-]+'

    
    # Find all matches for "A. Dickes" style sequences
    matches_abbr = re.findall(pattern_abbr, text)

    # Find all matches for full names including those with initials
    matches_full_name = re.findall(pattern_full_name, text)

    # Find all matches for multi-word capitalized sequences
    matches_multi_word = re.findall(pattern_multi_word, text)

    # Find all matches for names with prefixes like "de", "van", "von", "de la", etc.
    matches_prefix = re.findall(pattern_prefix, text)

    # Find all matches for general capitalized word sequences
    matches_general = re.findall(pattern_general, text)

    # Find all matches for pattern_initials_with_title sequences
    matches_pattern_initials_with_title = re.findall(pattern_initials_with_title, text)
    
    # Combine all matches into one list for multi-word capitalized sequences
    combined_matches_multi_word = set(matches_full_name + matches_multi_word + matches_prefix + matches_general+matches_pattern_initials_with_title)
    
    cr = []
    for each_item_c in combined_matches_multi_word:
        if len(each_item_c.split(" ")) > 1:
            cr.append(each_item_c)

    # Remove any matches that are already included in matches_abbr to avoid duplication
    combined_matches_multi_word = [match.strip() for match in cr if match.strip() not in matches_abbr]

    return matches_abbr, combined_matches_multi_word, matches_prefix, matches_full_name, matches_general


def clean(text_in):
    return re.sub(r'\s+', ' ', text_in).strip()

def clean_name(name):
    # Split the name into parts to handle the first word separately
    name = name.replace("MM ", "")
    parts = name.split()

    # Process only the first part to clean names
    first_part = parts[0]

    # Check if the first part has multiple consecutive uppercase letters and at least one lowercase letter
    index = 0
    for char in first_part:
        if char.isupper():
            index += 1
        else:
            break

    # If the first word has more than one consecutive uppercase letter and at least one lowercase, remove all but the last
    if index > 1 and any(char.islower() for char in first_part):
        first_part = first_part[index-1:]
    
    # Replace the first part in the list of parts
    parts[0] = first_part

    # Reassemble the cleaned parts into a single string
    cleaned_name = ' '.join(parts).strip()

    return cleaned_name

# Function to use the model to check if a text is a person's name
def is_person_name(name):
    prompt = (f"Determine if the following text is a person's name. "
              f"Consider potential typos or cultural variations in names: '{name}'. "
              f"Additionally, phrases such as 'Recueil Spécial' or 'Le Receveur' or 'Signatures Enregistré' are not names for people. "
              f"If the text is highly likely a person's name, answer 'yes'. Otherwise, answer 'no'.")
    
    # Tokenize and move to correct device
    inputs = tokenizer(prompt, return_tensors="pt").to(device)
    
    # Generate response on the same device
    outputs = model.generate(
        **inputs,
        max_new_tokens=30,
        temperature=0.2  # Lower randomness for consistent answers
    )
    
    response = tokenizer.decode(outputs[0], skip_special_tokens=True).replace("'yes'. Otherwise, answer 'no'.","")
    
    if "Answer:" in response:
        answer = response.split("Answer:")[-1].strip().lower()
    else:
        answer = response.strip().lower()
    
    return 'yes' in answer


# Read the file line by line with Latin-1 encoding

pathfiles = [
    '/JDH_PAPER/extracted_company_names.txt'
]

for file_path in pathfiles:
    
    write = open(file_path.replace(".txt", "_people.txt"), "w", encoding='utf-8')

    with open(file_path, 'r', encoding='utf-8') as file:
        for line in file:
            # Step 1: Strip the line and split using the specified delimiter "&&&***&&&"
            parts = line.strip().replace(" MM"," MM ").split('&&&****&&&')
            company = clean(parts[0])
            print("company: ", company)
            # Step 2: Extract the last item from the split parts
            last_part = clean(parts[-1]).strip()
            if "wrong" not in company.lower():
                # Step 3: Call the function to extract sequences
                list_abbr, list_multi_word, list_prefix, list_full_name, list_general = extract_sequences(last_part)
    
                # Step 4: Print the results for this line
                print("list_abbr: ", list_abbr)
                abb = ""
                for each_i in range(0, len(list_abbr) - 1):
                    list_abbr[each_i] = clean(list_abbr[each_i])
                    abb = abb + list_abbr[each_i] + " *_* "
                if len(list_abbr) > 0:
                    abb = abb + list_abbr[-1]
                print("abb: ", abb)
    
                print("list_multi_word: ", list_multi_word)
                filtered_names = [name for name in list_multi_word if is_person_name(name.replace("MM ", ""))]
                print(filtered_names)
                filtered_names_1=[]
                for Fil in filtered_names:
                    if Fil not in  filtered_names_1:
                        filtered_names_1.append(Fil)
                filtered_names=filtered_names_1
                print("filtered_names: ", filtered_names)
    
                fn = ""
                for each_i in range(0, len(filtered_names) - 1):
                    filtered_names[each_i] = clean(filtered_names[each_i])
                    filtered_names[each_i] = clean_name(filtered_names[each_i])
                    fn = fn + filtered_names[each_i] + " *_* "
                if len(filtered_names) > 0:
                    fn = fn + filtered_names[-1]
            else:
                fn=""
                abb=""
            print("fn: ", fn)
            print("***************************************************************************")

            fn = clean(fn)
            abb = clean(abb)

            print("******************")
            newline = company.replace('"',"") + " &&&***&&& " + company.replace('"',"") + " &&&***&&& " + fn + " &&&***&&& " + abb + " &&&***&&& " +\
            last_part + "\n"
            write.write(newline)
            write.flush()

            print("-" * 40)  # Separator for output clarity
    write.close()
print("done")
```

<!-- #region editable=true slideshow={"slide_type": ""} tags=["hermeneutics"] -->
Next, we explore another key component of the overall implementation: a pipeline for fine-tuning a GPT-2 model with enhanced capabilities for efficient training, response generation and model merging. This section complements the previous modules by introducing methods for adapting large language models to specific tasks using low-rank adaptation (LoRA), managing system resources effectively and integrating fine-tuned parameters into base models for flexible deployment. The process begins with class initialisation, where core attributes such as the dataset path, cache directory and Hugging Face authentication token are defined. A custom GPT-2 configuration is established by adjusting architecture parameters like hidden size, attention heads, number of layers, vocabulary size and activation function. Using this configuration, the tokeniser and model are loaded from Hugging Face, and the dataset—assumed to be in JSON format—is imported and prepared using the datasets library. Fine-tuning is carried out using LoRA, which allows selective updating of specific layers in the model to reduce training overhead. Training parameters, such as epoch count, batch size and logging intervals, are specified and passed to a supervised fine-tuning trainer, which handles the model training process. The fine-tuned model is saved to a designated output directory, with training metrics optionally tracked via TensorBoard. For inference, the pipeline includes a response generation method that constructs a prompt, tokenises it and produces a concise answer using the fine-tuned model. Generation behaviour is controlled through parameters like output length and temperature. The output is then decoded and cleaned to return a focused response. Resource management is addressed through a cleanup function that removes model components from memory and clears the GPU cache. Additionally, the code supports selective model merging, which involves loading both the base and fine-tuned models, comparing their parameters, and updating the base model with selected weights—ensuring compatibility before saving the merged model. This module fits into the larger architecture as a reusable and scalable fine-tuning pipeline that supports both training and inference. The following code block provides the full implementation of this component.
<!-- #endregion -->

```python editable=true slideshow={"slide_type": ""}
import gc
import torch
from datasets import load_dataset
from transformers import (
    AutoModelForCausalLM,
    AutoTokenizer,
    TrainingArguments,
    GPT2Config  # Import the GPT-2 configuration class
)
from peft import LoraConfig, PeftModel
from random import randrange
from trl import SFTTrainer  # Correct import for the SFTTrainer

class FineTune_GPT2:
    def __init__(self, dataset_path, cache_dir, token):
        """
        Initialize the FineTune_GPT2 class.

        Args:
            dataset_path (str): Path to the dataset.
            cache_dir (str): Directory to cache the models and tokenizers.
            token (str): Hugging Face API token for accessing gated repositories.

        How to obtain the Hugging Face API token:
        1. Go to https://huggingface.co/settings/tokens
        2. Log in or sign up if you don't have an account.
        3. Create a new token with the required permissions (read access is sufficient).
        4. Copy the token and provide it when initializing this class.
        """
        self.dataset_path = dataset_path
        self.cache_dir = cache_dir
        self.token = token

        # Embedded configuration
        config_dict = {
            "architectures": ["GPT2LMHeadModel"],
            "bos_token_id": 50256,
            "eos_token_id": 50256,
            "hidden_act": "gelu_new",
            "hidden_size": 768,
            "initializer_range": 0.02,
            "intermediate_size": None,
            "layer_norm_eps": 1e-05,
            "model_type": "gpt2",
            "num_attention_heads": 12,
            "num_hidden_layers": 12,
            "vocab_size": 50257
        }
        self.config = GPT2Config.from_dict(config_dict)  # Use the correct configuration class

        self.tokenizer = AutoTokenizer.from_pretrained(
            "gpt2", 
            cache_dir=self.cache_dir, 
            use_auth_token=self.token  # Use the correct parameter
        )
        self.tokenizer.pad_token = self.tokenizer.eos_token  # Set padding token to eos token
        self.tokenizer.padding_side = 'right'  # Ensure padding is on the right
        self.trained_model = AutoModelForCausalLM.from_pretrained(
            "gpt2", 
            config=self.config,
            cache_dir=self.cache_dir,
            use_auth_token=self.token  # Use the correct parameter
        ).to("cuda")
        self.dataset = load_dataset('json', data_files=self.dataset_path, split='train')

    def train_model(self, output_dir, num_train_epochs=3, per_device_train_batch_size=2, per_device_eval_batch_size=1, max_seq_length=None):
        lora_config = LoraConfig(
            lora_alpha=16,
            lora_dropout=0.1,
            r=64,
            target_modules=[
                "attn.c_attn",
                "attn.c_proj",
                "mlp.c_fc",
                "mlp.c_proj",
            ],
            bias="none",
            task_type="CAUSAL_LM",
        )

        training_args = TrainingArguments(
            output_dir=output_dir,
            num_train_epochs=num_train_epochs,
            per_device_train_batch_size=per_device_train_batch_size,
            per_device_eval_batch_size=per_device_eval_batch_size,
            logging_dir=f"{output_dir}/logs",
            logging_steps=10000,
            save_steps=1000,
            warmup_ratio=0.03,
            report_to="tensorboard"
        )

        trainer = SFTTrainer(
            model=self.trained_model,
            train_dataset=self.dataset,
            peft_config=lora_config,
            dataset_text_field="text",  # Assuming 'text' is the field name containing the text data
            max_seq_length=max_seq_length,  # Pass None or specify a maximum sequence length
            tokenizer=self.tokenizer,
            args=training_args
        )

        trainer.train()
        trainer.model.save_pretrained(output_dir)
        print("The new model is available in " + output_dir)
        self.trained_model = trainer.model

    def generate_response(self, question, max_new_tokens=500, temperature=0.1):
        prompt = f"""You will be provided with a question. You must provide only a single answer. You must not provide additional questions and answers.
        Question:
        {question}
        """
        model_input = self.tokenizer(prompt, return_tensors="pt").to("cuda")
        with torch.no_grad():
            generated_code = self.trained_model.generate(**model_input, max_new_tokens=max_new_tokens, pad_token_id=self.tokenizer.eos_token_id, temperature=temperature)
            generated_code = self.tokenizer.decode(generated_code[0], skip_special_tokens=True)
            response = generated_code.split("You will be provided with a question")[1]
            if len(response) < 10:
                return generated_code
        return response

    def clean_up(self):
        del self.tokenizer
        del self.trained_model
        gc.collect()
        torch.cuda.empty_cache()

    def selective_merge(self, base_model_path, fine_tuned_model_path, output_dir):
        base_model = AutoModelForCausalLM.from_pretrained(base_model_path, cache_dir=self.cache_dir, use_auth_token=self.token).to("cuda")
        fine_tuned_model = AutoModelForCausalLM.from_pretrained(fine_tuned_model_path, cache_dir=self.cache_dir, use_auth_token=self.token).to("cuda")

        # Extract state dicts
        base_state_dict = base_model.state_dict()
        ft_state_dict = fine_tuned_model.state_dict()

        # Filter out keys: only update base model with keys that exist in its state dict and have the same size
        for key in ft_state_dict:
            if key in base_state_dict and ft_state_dict[key].size() == base_state_dict[key].size():
                base_state_dict[key] = ft_state_dict[key]

        # Load the filtered state dict back into the base model
        base_model.load_state_dict(base_state_dict, strict=False)

        # Save the merged model
        base_model.save_pretrained(output_dir)

        # Save tokenizer and configuration as well
        self.tokenizer.save_pretrained(output_dir)
        self.config.save_pretrained(output_dir)

        print(f"Merged model, tokenizer, and config are saved in {output_dir}")

        return base_model



# Instantiate and use the FineTune_GPT2 class
dataset_path = "/JDH_PAPER/training.jsonl"
hf_token = "............." # your token
cache_dir = "/JDH_PAPER"
output_dir = "/JDH_PAPER/Models/"
merged_model_output_dir = "/JDH_PAPER/Merged"

# Create an instance of FineTune_GPT2 and start training
fine_tuner = FineTune_GPT2(dataset_path, cache_dir, token=hf_token)


# Train the model and save it to the output directory
fine_tuner.train_model(output_dir=output_dir, num_train_epochs=25, per_device_train_batch_size=2, per_device_eval_batch_size=1)

# Optionally, merge the fine-tuned model with the base model
fine_tuner.selective_merge(base_model_path=output_dir, fine_tuned_model_path=output_dir, output_dir=merged_model_output_dir)


```

<!-- #region editable=true slideshow={"slide_type": ""} tags=["hermeneutics"] -->
Building on the previous components, this section demonstrates how a fine-tuned GPT-2 model is used to extract addresses from unstructured text through a complete pipeline of preprocessing, inference and post-processing. The process begins by initialising a class that loads the tokeniser and model from a specified directory, using a Hugging Face token and memory-efficient settings such as half-precision (torch.float16) and right-side padding for token alignment. To guide the model’s output, the code constructs a question-style prompt, which is tokenised and passed through the model using controlled generation parameters like maximum token length and temperature for deterministic responses. The output is then decoded and cleaned to remove special tokens or redundant text. Input is read from a structured file where each line contains company data. Each line is split using a custom delimiter, and the relevant portion is extracted to form the prompt. The generated response is then processed using regex to isolate the address, clean it and apply fallback logic in cases where a valid address cannot be determined. Following address extraction, the output undergoes an additional cleaning stage to enhance readability, and results are written to a new file with consistent formatting. The code includes error-handling procedures that reinitialise the model if failures occur and employs memory management techniques such as garbage collection and GPU cache clearing. This module integrates seamlessly into the larger system, handling input, generating and refining address data, and producing clean, structured output ready for further analysis.
<!-- #endregion -->

```python editable=true slideshow={"slide_type": ""}
from transformers import AutoModelForCausalLM, AutoTokenizer
import gc
import torch
import os,re


class FineTune_GPT2_use:
    def __init__(self, cache_dir=None, token=None, model_path=None):
        """
        Initialize the class with cache_dir, token, and model_path for the GPT2 model.
        """
        self.cache_dir = cache_dir
        self.token = token

        # Load the tokenizer and model from the specified path (fine-tuned model folder)
        self.tokenizer = AutoTokenizer.from_pretrained(model_path, cache_dir=self.cache_dir, token=self.token)

        # Load the model on CPU for debugging, or on CUDA with float16 if memory is an issue
        self.trained_model = AutoModelForCausalLM.from_pretrained(
            model_path, 
            cache_dir=self.cache_dir, 
            token=self.token, 
            torch_dtype=torch.float16  # Try using float16 to reduce memory
        ).to("cuda")

        # Set padding token for the tokenizer
        # self.tokenizer.pad_token = self.tokenizer.eos_token
        self.tokenizer.padding_side = 'right'

    def generate_response(self, question, max_new_tokens=500, temperature=0.1):
        """
        Generate a response to the given question using the fine-tuned GPT2 model.

        Args:
            question (str): The question to ask the model.
            max_new_tokens (int): Maximum number of tokens to generate.
            temperature (float): The temperature for generation.

        Returns:
            str: The generated response.
        """
        device = "cuda" if torch.cuda.is_available() else "cpu"

        # Tokenize the input and print for debugging
        inputs = self.tokenizer(question, return_tensors="pt", truncation=True, max_length=1024)
        inputs = inputs.to(device)  # Move inputs to the same device as the model

        # Generate text with no gradient computation
        with torch.no_grad():
            generated_output = self.trained_model.generate(
                **inputs, 
                max_new_tokens=max_new_tokens, 
                pad_token_id=self.tokenizer.eos_token_id, 
                temperature=temperature
            )
            # Decode the generated text and remove special tokens
            generated_text = self.tokenizer.decode(generated_output[0], skip_special_tokens=True)

        return generated_text

    def clean_up(self):
        """
        Clean up the resources by deleting the model and tokenizer, and clearing the GPU cache.
        """
        del self.tokenizer
        del self.trained_model
        gc.collect()
        torch.cuda.empty_cache()

# Run the model on CPU or GPU with debug options to find the problem
if __name__ == "__main__":
    gpt2_model_path = "/JDH_PAPER/Merged/"
    fine_tuner1 = FineTune_GPT2_use(cache_dir='/JDH_PAPER', token='use_your_token', model_path=gpt2_model_path)
    pathfiles = [
        '/JDH_PAPER/extracted_company_names_people.txt'
    ]
#     question = "Where is the address of the company in the following text?"
#     response = fine_tuner.generate_response(question)
#     print("response:",response)
    for each_fine in pathfiles:
        dataset_path = each_fine.replace("_people.txt", "_people_Addr.txt")
        write = open(dataset_path, "w", encoding='utf-8')
        read_file = each_fine

        read = open(read_file, 'r', encoding='utf-8')
        for line in read:
            # Process each line and extract relevant information
            L = line.split(" &&&***&&& ")
            L[-1]=L[-1].rstrip().lstrip().strip()
            CopyL=L[-1]
            L[-1] = L[-1].split("+++++++++++++++++")[-1].replace(" : ", ": ")

            # Step 1: Use GPT-2 fine-tuned model to find address in text
            te=""
            size_L=50
            if len(L[-1].split(" "))<50:
                size_L=len(L[-1].split(" "))
            for e in range(0,size_L):
                te=te+L[-1].split(" ")[e]+" "
            question="Where is the address of the company in the following text? "+te 
            print("question: ",question)
            try:
                address=fine_tuner1.generate_response(question)
            except:
                del fine_tuner1
                fine_tuner1 = FineTune_GPT2_use(cache_dir='/JDH_PAPER/', token='your_token', model_path=gpt2_model_path)

            address = re.sub(r'\s+', ' ', address)  # Clean the response
            
            try:
                # Extract address, handle missing or incorrect data gracefully
                address = re.sub(r'\s+', ' ', address).split("Answer:")[1].replace("The Address is :", "").replace("</s>", "").replace("</s", "").replace("/s>", "")
            except:
                print("To be checked: ", address)
                address = "No Addr"

            address = re.sub(r'\s+', ' ', address)
            address=re.sub(r"(?<!^)(?=[A-Z])", " ", address)
            address = re.sub(r'\s+', ' ', address)  # Clean the response
            if len(address)>120:
                address="No Addr"

            refined_address = address  # Refinement step could be added here
            print("++++++++++")
            print("refined address:", refined_address)
            print("++++++++++")
            print("=====================================================================")

            # Write results back to the file
            newline = L[0]+" &&&***&&& "+L[1]+" &&&***&&& "\
            +L[2]+" &&&***&&& "+L[3]+" &&&***&&& "+refined_address+" &&&***&&& "+CopyL.replace('\n', '')+"\n"

            write.write(newline)
            write.flush()

        write.close()
        read.close()

        # Clean up resources after processing
        fine_tuner1.clean_up()
    
```

<!-- #region editable=true slideshow={"slide_type": ""} tags=["hermeneutics"] -->
Expanding the capabilities of the pipeline, this module focuses on identifying and extracting country names from text using a multilingual dictionary and regex-based matching. A predefined dictionary maps country names and their variations in English, French, German and Luxembourgish. The code reads an input file containing company information, splits each line into structured components using a custom delimiter, and applies text cleaning to normalise whitespace. For each line, it scans the relevant text component—typically a description or address—against all known country name variations. A "for loop" is used to match standalone country names while avoiding partial matches, with special handling to distinguish cases like “Jersey” and “New Jersey” based on frequency. Extracted country names are deduplicated and formatted using a custom separator before being appended to the original data. The processed results are written to a new output file in a structured format, ensuring compatibility with downstream tasks. Throughout execution, the code prints intermediate values such as company names, matched text and identified countries for verification. This module adds robust, multilingual country name extraction to the processing pipeline, with careful handling of edge cases and clear formatting for analysis.
<!-- #endregion -->

```python editable=true slideshow={"slide_type": ""}
file="/JDH_PAPER/extracted_company_names_people_Addr.txt"
read=open(file,"r",encoding="utf-8")
write=open("/JDH_PAPER/final_a.txt","w",encoding="utf-8")
import re
for line in read:
    L=line.split("&&&***&&&")
    names_c=[]
    for i in range(0, len(L)):
        L[i] = re.sub(r'\s+', ' ', L[i]).strip()
    string_name_co=" "
    if "wrong" in L[0].lower():
        pass
    else:
        found = set()
        for english_name, variants in countries.items():
            all_variants = set(variant.lower() for variant in variants + [english_name])
    
            if english_name == "Jersey":
                if is_clean_match(normalized_text, "jersey") and not is_clean_match(normalized_text, "new jersey"):
                    found.add("Jersey")
                    JJCC += 1
            else:
                for variant in all_variants:
                    if is_clean_match(normalized_text, variant):
                        found.add(english_name)

        names_c=list(found)
        for e in names_c:
            string_name_co=string_name_co+e+" *_* "
        string_name_co=re.sub(r'\s+', ' ', string_name_co).strip()[:-4]
    newline=""
    for i in range(0,len(L)-1):
       newline=newline+L[i]+" &&&***&&& " 
    newline=newline+string_name_co+" &&&***&&& " +L[-1]
    newline=re.sub(r'\s+', ' ', newline).strip()
    print("Company: \n ",L[0])
    print("Description: \n ",L[-1].split("+++++++++++++++++")[-1])
    print("++++++++")
    print("Countries:")
    print(string_name_co)
    print("++++++++")

    print("****************************************************************************************************")

    write.write(newline.replace("\n","")+"\n")
    write.flush()
write.close()
print("done")
```

<!-- #region editable=true slideshow={"slide_type": ""} tags=["hermeneutics"] -->
As part of the people extraction pipeline, an additional improvement step is introduced to enhance data consistency by removing formal titles from extracted person names. This refinement ensures that names are cleaned before entering the loading phase, eliminating job titles, honorifics and linguistic variations that can introduce noise in downstream analysis. The cleaning process begins with a function to remove excess whitespace, using regular expressions to replace multiple spaces with a single space and trimming any leading or trailing characters. The core of the enhancement lies in the title removal function, which relies on a comprehensive, multilingual list of titles, including English, French, German, Luxembourgish, Spanish and Portuguese variants. A flexible regex pattern is constructed to match these titles as standalone words, accounting for optional punctuation and accented characters. Matches are removed in a case-insensitive and Unicode-aware manner to ensure robustness across languages. Once processed, the names are returned in a clean, title-free format. For example, inputs such as “Dr John Doe”, “Monsieur Jean Dupont” or “Herr Karl Müller” are standardised to “John Doe”, “Jean Dupont” and “Karl Müller” respectively. This step significantly improves the uniformity and accuracy of person name data, simplifies further processing and adapts easily to multilingual contexts. Integrated directly before the loading stage, this module ensures that only properly cleaned names are included in the final dataset, contributing to overall data quality and reliability within the pipeline.
<!-- #endregion -->

```python editable=true slideshow={"slide_type": ""}
def remove_extra_spaces(text):
    # Use regular expression to replace multiple spaces with a single space
    cleaned_text = re.sub(r'\s+', ' ', text)
    # Strip leading and trailing spaces
    cleaned_text = cleaned_text.strip()
    return cleaned_text
    
def remove_titles(name):
    import re

    # List of common titles in English, French, German, Luxembourgish, Spanish, and Portuguese
    titles = [
        # English Titles
        r'\bMr\b', r'\bMrs\b', r'\bMs\b', r'\bMiss\b', r'\bDr\b', r'\bProf\b', r'\bSir\b',
        r'\bMadam\b', r'\bLord\b', r'\bLady\b', r'\bRev\b', r'\bHon\b', r'\bJudge\b',
        r'\bDame\b', r'\bCapt\b', r'\bCol\b', r'\bGen\b', r'\bLt\b', r'\bMaj\b',
        r'\bSgt\b', r'\bCpl\b', r'\bPvt\b', r'\bChief\b', r'\bOfficer\b', r'\bDetective\b',
        r'\bAttorney\b', r'\bAmb\b', r'\bConsul\b', r'\bSec\b', r'\bDir\b', r'\bMgr\b',
        r'\bCEO\b', r'\bCFO\b', r'\bCTO\b', r'\bPresident\b', r'\bVP\b', r'\bDep\b',

        # French Titles
        r'\bMonsieur\b', r'\bMadame\b', r'\bMademoiselle\b', r'\bMlle\b', r'\bMme\b', r'\bMaître\b',r'\bMaitre\b',r'\bTissus\b',
        r'\bDocteur\b', r'\bProfesseur\b', r'\bPrésident\b', r'\bVice-président\b', r'\bSecrétaire\b',r'\bLuxembourg\b',r'\bMaitre\b',
        r'\bDirecteur\b', r'\bPDG\b', r'\bAdministrateur\b', r'\bComte\b', r'\bComtesse\b', r'\bComptes\b',r'\bBelgique\b'
        r'\bMarquis\b', r'\bMarquise\b', r'\bDuc\b', r'\bDuchesse\b', r'\bPrince\b', r'\bPrincesse\b',
        r'\bMïster\b', r'\bMessieurs\b', # Mister with an ï (for completeness)

        # German Titles
        r'\bHerr\b', r'\bFrau\b', r'\bFräulein\b', r'\bHr\b', r'\bFr\b', r'\bDoktor\b',
        r'\bProfessor\b', r'\bPräsident\b', r'\bVizepräsident\b', r'\bSekretär\b',
        r'\bDirektor\b', r'\bVerwalter\b', r'\bKanzler\b', r'\bBaron\b', r'\bBaronin\b',
        r'\bGraf\b', r'\bGräfin\b', r'\bFürst\b', r'\bFürstin\b', r'\bHerzog\b', r'\bHerzogin\b',

        # Luxembourgish Titles
        r'\bHär\b', r'\bMadame\b', r'\bMademoiselle\b', r'\bDokter\b', r'\bProfesser\b',
        r'\bBuergermeeschter\b', r'\bPrinz\b', r'\bPrinzessin\b', r'\bGroßherzog\b', r'\bGroßherzogin\b',

        # Spanish Titles
        r'\bSeñor\b', r'\bSeñora\b', r'\bSeñorita\b', r'\bDr\b', r'\bDra\b', r'\bProf\b', r'\bProfa\b',
        r'\bDon\b', r'\bDoña\b', r'\bLicenciado\b', r'\bLicenciada\b', r'\bIngeniero\b',
        r'\bIngeniera\b', r'\bPresidente\b', r'\bVicepresidente\b', r'\bDirector\b',
        r'\bAdministradora\b', r'\bAlcalde\b', r'\bAlcaldesa\b',

        # Portuguese Titles
        r'\bSenhor\b', r'\bSenhora\b', r'\bSenhorita\b', r'\bDoutor\b', r'\bDoutora\b',
        r'\bProfessor\b', r'\bProfessora\b', r'\bEngenheiro\b', r'\bEngenheira\b',
        r'\bPresidente\b', r'\bVice-presidente\b', r'\bDiretor\b', r'\bDiretora\b',
        r'\bAdministrador\b', r'\bAdministradora\b', r'\bPrefeito\b', r'\bPrefeita\b'
    ]

    # Create a regex pattern that matches any of the titles (including accented characters)
    pattern = re.compile(r'\b(?:' + '|'.join(titles) + r')\.?', re.IGNORECASE | re.UNICODE)

    # Substitute the titles with an empty string
    name_without_titles = re.sub(pattern, '', name).strip()
    return name_without_titles
import re
read=open("/JDH_PAPER/final_a.txt","r",encoding="utf-8")
write=open("/JDH_PAPER/final_a.txt".replace("_a.txt","_c.txt"),"w",encoding="utf-8")

delimiter="&&&***&&&"
count=0
for line in read:
    L=line.split(delimiter)
    L[2]=remove_extra_spaces(L[2]).rstrip().lstrip().strip()
    print("Input names: ",L[2])
    print()
    newL2=L[2].split(" *_* ")

    PEOPLE=[]
    output_name=[]
    for index in range(0,len(newL2)):
        newL2[index]=remove_titles(remove_extra_spaces(newL2[index]).lstrip().rstrip().strip())
        if len(newL2[index].split(" "))>1:
            if len(newL2[index].split(" ")[-1])>2:
                output_name.append(remove_extra_spaces(newL2[index]).lstrip().rstrip().strip())
    print("Cleaned names: ",output_name)
    newline=""
    for i in range(0,len(L)-1):
        if i!=2:
            newline=newline+L[i]+" "+delimiter+" "

        else:
            output_string=""
            for each_n in output_name:
                output_string=output_string+each_n+" *_* "
            output_string=output_string[:-4].lstrip().rstrip().strip()
            print("output_string:",output_string)
            newline=newline+output_string+" "+delimiter+" "
    newline=newline+L[-1]
    write.write(newline)
    write.flush()
    print()
    print("*************************************************")
read.close()
write.close()
```

## Load

<!-- #region editable=true slideshow={"slide_type": ""} tags=["hermeneutics"] -->
To complete the ETL pipeline, the final step involves loading the processed and cleaned data into a relational database, ensuring both data integrity and the establishment of meaningful relationships between entities such as companies, addresses, individuals, countries and messages. This stage begins by connecting to a SQL Server database using pyodbc, with secure authentication and error handling to validate connectivity. For efficiency, the implementation preloads existing records into in-memory dictionaries, reducing redundant queries by caching entity IDs. Before insertion, values are standardised using cleaning functions to ensure consistency. Helper methods manage the insertion or retrieval of primary keys by first checking for existing entries and inserting new ones only when necessary. These keys are then used to establish associations across multiple junction tables, supporting complex many-to-many relationships. The pipeline processes an input file line by line, splitting each record into structured components using a custom delimiter. Company names, alternative names, addresses, person names and countries are extracted, cleaned and matched against the database. When a match is found or inserted, corresponding IDs are retrieved and used to link data across the relational schema. Descriptions are recorded in a messages table and connected to relevant entities via junction tables. Special handling is included to manage address length limits and ambiguous company names. The code dynamically adjusts to different file encodings and logs errors during any part of the process
—such as file reading, database operations or line parsing—, ensuring that individual failures do not interrupt the overall workflow. Upon successful processing, the data is committed to the database, and all resources are properly released. By preventing duplicates, maintaining clean formatting and efficiently linking entities, this step finalises the ETL pipeline with a scalable and resilient approach to structured data integration, enabling robust querying and downstream analytical tasks.
<!-- #endregion -->

```python editable=true slideshow={"slide_type": ""}
import pyodbc

# Define your connection string with the correct credentials and server information
conn_str = 'DRIVER={ODBC Driver 17 for SQL Server};SERVER=10.184.4.29;DATABASE=LETTER;UID=c2dh;PWD=C2dh4ever'

# Establish the connection
try:
    conn = pyodbc.connect(conn_str)
    cursor = conn.cursor()
    print("Connection successful")
except pyodbc.Error as e:
    print(f"Error connecting to the database: {e}")
    raise

# List of tables to delete from
# Note: Order matters - delete from the junction tables first to avoid foreign key constraint violations
tables = [
    'People_Addresses',
    'People_Companies',
    'People_Countries',
    'People_MessagesL',
    'Addresses_Countries',
    'Companies_Countries',
    'People',
    'Addresses',
    'Companies',
    'Countries',
    'MessagesL',
]

# Function to delete all rows from the tables
def delete_all_data():
    try:
        for table in tables:
            print(f"Deleting data from {table}...")
            cursor.execute(f"DELETE FROM {table}")  # Using DELETE to respect foreign key constraints
            conn.commit()
            print(f"Data deleted from {table}")
    except pyodbc.Error as e:
        print(f"Error deleting data from {table}: {e}")
        raise

# Run the delete process
delete_all_data()

# Close the connection
cursor.close()
conn.close()
print("Connection closed")
import pyodbc
import re
import traceback


def has_column(table, column):
    """
    Check if a column exists in a specific table.
    """
    try:
        cursor.execute("""
            SELECT 1
            FROM INFORMATION_SCHEMA.COLUMNS
            WHERE TABLE_NAME = ? AND COLUMN_NAME = ?
        """, table, column)
        return cursor.fetchone() is not None
    except pyodbc.Error as e:
        print(f"Error checking column {column} in table {table}: {e}")
        return False


def assign_unused_id(table, id_column):
    """
    Retrieve the next unused ID for a given table and column.
    """
    try:
        cursor.execute(f"SELECT MAX({id_column}) FROM {table}")
        max_id = cursor.fetchone()[0]
        return (max_id or 0) + 1
    except pyodbc.Error as e:
        print(f"Error fetching max ID from {table}: {e}")
        raise


def insert_or_get_id(table, column, value, year=None, id_column=None):
    """
    Insert a new record or retrieve the ID of an existing record.
    """

    if not id_column:
        id_column = f"{table[:-1]}_id"

    try:
        # Check if the record already exists
        query = f"SELECT {id_column} FROM {table} WHERE {column} = ?"
        params = [value]
        if has_column(table, "year"):
            query += " AND year = ?"
            params.append(year)

        cursor.execute(query, params)
        row = cursor.fetchone()

        # Return the ID if the record exists
        if row:
            return row[0]

        # Assign new ID
        new_id = assign_unused_id(table, id_column)

        # Insert new record
        columns = [id_column, column]
        values = [new_id, value]
        placeholders = ["?", "?"]

        if has_column(table, "year") and year is not None:
            columns.append("year")
            values.append(year)
            placeholders.append("?")

        if has_column(table, "effective_start_date"):
            columns.append("effective_start_date")
            placeholders.append("?")
            values.append("1970-01-01")  # Default start date

        if has_column(table, "is_current"):
            columns.append("is_current")
            placeholders.append("?")
            values.append(1)  # Default value for is_current

        if has_column(table, "current_version"):
            columns.append("current_version")
            placeholders.append("?")
            values.append(1)  # Default version for new records

        insert_query = f"INSERT INTO {table} ({', '.join(columns)}) VALUES ({', '.join(placeholders)})"
        cursor.execute(insert_query, values)
        conn.commit()

        return new_id

    except pyodbc.Error as e:
        print(f"Error inserting or retrieving ID from {table} for value '{value}': {e}")
        return None


def insert_into_junction(table, col1, col2, year, id1, id2):
    """
    Insert or update a relationship in a junction table using SCD Type 2 logic.
    """
    try:
        # Check if an active record exists
        cursor.execute(f"""
            SELECT is_current, effective_start_date, effective_end_date
            FROM {table}
            WHERE {col1} = ? AND {col2} = ? AND year = ?
        """, id1, id2, year)
        row = cursor.fetchone()

        if row and row[0] == 1:  # Active record exists
            return  # No need to update

        if row:  # Inactivate the existing record
            cursor.execute(f"""
                UPDATE {table}
                SET is_current = 0, effective_end_date = GETDATE()
                WHERE {col1} = ? AND {col2} = ? AND year = ? AND is_current = 1
            """, id1, id2, year)
            conn.commit()

        # Insert the new record
        cursor.execute(f"""
            INSERT INTO {table} ({col1}, {col2}, year, is_current, effective_start_date, effective_end_date)
            VALUES (?, ?, ?, 1, GETDATE(), NULL)
        """, id1, id2, year)
        conn.commit()
    except pyodbc.Error as e:
        print(f"Error inserting into {table} (col1={col1}, col2={col2}, year={year}): {e}")
        raise



def process_file(path_file):
    """
    Process the input file and populate the database with its data.
    """
    try:
        line_number=0
        with open(path_file, 'r', encoding='utf-8') as file:
            for line in file:
                # Split the line into columns
                columns = line.strip().split(' &&&***&&& ')
                # Extract the data from the line
                year = int(columns[0].strip())
                company_name = columns[1]
                address = columns[3]
                
                country_name = columns[7].split("*_*")
                for index_country in range(0,len(country_name)):
                    country_name[index_country]=country_name[index_country].rstrip().lstrip().strip()
                
                person_name = columns[5].split("*_*")
                for person_index in range(0,len(person_name)):
                    person_name[person_index]=person_name[person_index].rstrip().lstrip().strip()

                try:
                    person_name.remove('')
                except:
                    pass

                try:
                    person_name.remove('')
                except:
                    pass
                
                if "wrong" in company_name.lower():
                    continue
                else:
                # Insert or retrieve the IDs
                    country_ids=[]
                    person_ids=[]
                    
                    company_id = insert_or_get_id('Companies', 'company_name', company_name, year, 'company_id')
                    address_id = insert_or_get_id('Addresses', 'address_description', address, year, 'address_id')

                    for country in country_name:
                        country_id = insert_or_get_id('Countries', 'country_name', country, year, 'country_id')
                        country_ids.append(country_id)
                            
                    for person in person_name:
                        person_id = insert_or_get_id('People', 'person_name', person, year, 'person_id')
                        person_ids.append(person_id)
                            
                    # Insert into junction tables
                    for country_id in country_ids:
                        if company_id and country_id:
                            print("company_id:",company_id)
                            print("country_id:",country_id)
                            insert_into_junction('Companies_Countries', 'company_id', 'country_id', year, company_id, country_id)
                        if address_id and country_id:
                            insert_into_junction('Addresses_Countries', 'address_id', 'country_id', year, address_id, country_id)

                    for person_id in person_ids:
                        if person_id and company_id:
                            insert_into_junction('People_Companies', 'person_id', 'company_id', year, person_id, company_id)
                        if person_id and address_id:
                            insert_into_junction('People_Addresses', 'person_id', 'address_id', year, person_id, address_id)

                    
                    print("line_number:",line_number)
                line_number=line_number+1

    except FileNotFoundError:
        print(f"File not found: {path_file}")
    except pyodbc.Error as e:
        print(f"Database error while processing file: {e}")
    except Exception as e:
        print(f"Unexpected error: {e}")


if __name__ == "__main__":
    conn_str = 'DRIVER={ODBC Driver 17 for SQL Server};SERVER=10.184.4.29;DATABASE=LETTER;UID=c2dh;PWD=C2dh4ever'

    for year in range(1970, 1971):
        try:
            conn = pyodbc.connect(conn_str)
            cursor = conn.cursor()
            print(f"Processing data for year {year}...")
            path_file = f"../FILE_IMPORT/{year}_final_2ADDR_final_check_c.txt"
            process_file(path_file)
        except Exception as e:
            print(f"Error: {e}")
        finally:
            try:
                cursor.close()
                conn.close()
            except Exception:
                pass

```

# Hyperlocalized geographies: shell companies in Luxembourg

<!-- #region citation-manager={"citations": {"899wo": [{"id": "6915743/99Z4RH8W", "source": "zotero"}]}} editable=true slideshow={"slide_type": ""} -->
During his first campaign to become President of the United States in 2008, Barack Obama referred to Ugland House in George Town, Cayman Islands, in several of his speeches. Described by the future US President as “either the biggest building in the world or the biggest tax scam in the world” <cite id="899wo"><a href="#zotero%7C6915743%2F99Z4RH8W">(Davis, 2009)</a></cite>, the headquarters of the law firm Maples Group (previously Maples and Calder) is the registered office of numerous companies. While the number of companies supposedly housed in the building varies greatly in the press—from 18,000 to 40,000—, it is clear that the Maples headquarters, which was also present in Luxembourg from 2007 onwards, first as a financial service provider (specialised fiduciary services, fund management, entity formation and management, insurance management, etc.) and then as a law firm from 2018, hosted thousands of companies (see “Le groupe Maples se développe au Grand-Duché”, 2018).
<!-- #endregion -->

<!-- #region editable=true slideshow={"slide_type": ""} -->
## Shell companies in the center of the financial sector (1929-1960)
<!-- #endregion -->

<!-- #region editable=true slideshow={"slide_type": ""} -->
Most offshore financial centres have their “Ugland House”, and Luxembourg is no exception. In order to map this phenomenon and follow it over time (Figure 3), we proceeded in two ways. For the years 1929-1959, we built a database of holdings. For the years 1960-2016, a different method to identify the most relevant addresses for shell companies was used (see below).
<!-- #endregion -->

```python editable=true slideshow={"slide_type": ""} tags=["figure-heatmap-*"]
from IPython.display import IFrame
metadata={
    "jdh": {
        "module": "object",
        "object": {
            "type":"image",
            "source": [
                "Fig. 3. Time-series heat map illustrating the spatial and temporal evolution of financial addresses in Luxembourg City from 1929 to 2016. The animation shows how the intensity and geographic focus of development shifted over eight distinct time periods, with colors ranging from blue (low intensity) to red (high intensity)."
            ]
        }
    }
}
display(IFrame(src='./media/heatmap_temporal_all.html', width=800, height=600), metadata=metadata)
```

<!-- #region citation-manager={"citations": {"qjiam": [{"id": "6915743/HVMKF47G", "source": "zotero"}], "vdl4j": [{"id": "6915743/DNV4AN63", "source": "zotero"}], "z72xs": [{"id": "6915743/MTBV75MR", "source": "zotero"}]}} editable=true slideshow={"slide_type": ""} -->
We can highlight three elements from Figure 3. First, the financial centre that emerged between the World Wars is hyper-localised. The vast majority of holdings had their headquarters within a one-kilometre perimeter, concentrated around Boulevard Royal, which was constructed in the 1870s following the dismantling of the fortress. In the interwar period, Luxembourg City was a small town of around 50,000 inhabitants. Several banks settled on this prestigious avenue, which was home to a number of private villas as well as the country’s first financial institutions in the early 20th century. Political, cultural and economic activities took place in an extremely concentrated geographical area <cite id="qjiam"><a href="#zotero%7C6915743%2FHVMKF47G">(Philippart, 2006)</a></cite><cite id="vdl4j"><a href="#zotero%7C6915743%2FDNV4AN63">(<i>Philippart - 2006 - Luxembourg, de l’historicisme Au Modernisme. De La Ville Forteressse à La Capitale Nationale.Pdf</i>, n.d.)</a></cite><cite id="z72xs"><a href="#zotero%7C6915743%2FMTBV75MR">(Weber, 2013)</a></cite>, so it is no surprise that it was also here that the emerging holding market took off.
<!-- #endregion -->

<!-- #region citation-manager={"citations": {"m9fmb": [{"id": "6915743/M3M2TDWJ", "source": "zotero"}], "z427c": [{"id": "6915743/6MGDHU8G", "source": "zotero"}]}} editable=true slideshow={"slide_type": ""} -->
Second, when linking addresses to companies, it appears that in the years leading up to the Second World War, the market for holding company domiciliation was dominated by banks. Among the five most used addresses between 1929 and 1939, four are the headquarters of banks. Banking was a shaky business in Luxembourg in the second half of the 19th century, with several bankruptcies and the few banks remaining relatively small <cite id="z427c"><a href="#zotero%7C6915743%2F6MGDHU8G">(Anders, 1928)</a></cite>. After the First World War, French and Belgian capital was invested in the Luxembourgish banking market, so that by the end of the 1920s when the holding law was adopted in parliament, the country had about fifteen banking institutions. Four of them became players in the holding company market: Banque Internationale à Luxembourg (BIL), which held 42% of the holding company headquarters for which the address is known, Banque Commerciale (19%), Banque Lévy (14%) and Banque Générale du Luxembourg (BGL), which only entered the holding market in 1936, with 6%. Apart from BIL, which was founded in 1856, the other three banks had been established after World War One: BGL in 1919, Banque Commerciale in 1921, and Banque Alfred Lévy in 1926. Among the five most used addresses that served as headquarters for holding companies is also that of a notary, Paul Kuborn. Alongside banks, notaries played an important role as financial service providers in Luxembourg as they offered several banking services, especially for private individual clients, and several notaries also played an important role in the nascent emerging shell company market. Of the 32 notaries authorised to practise during the 1930s, five specialised in drafting holding company deeds, a lucrative business at a time when the notarial profession was going through a serious crisis, with several firms being liquidated because they had engaged in disastrous financial activities <cite id="m9fmb"><a href="#zotero%7C6915743%2FM3M2TDWJ">(Majerus, 1949)</a></cite>(2:822). Among the five notaries that were present on this market, Paul Kuborn was the most prolific: between 1929 and 1939, nearly a quarter of the holdings were documented by his firm. He had close links with BIL, for which he managed most holding company registrations, and he also provided the whole range of domiciliation services (address, sham directors, etc.). While other notaries sometimes used their clerks as sham directors—since they themselves were prohibited from performing such functions—, they rarely offered their office addresses as holding company headquarters.
<!-- #endregion -->

<!-- #region citation-manager={"citations": {"ouet6": [{"id": "6915743/ZANTZ8SS", "source": "zotero"}]}} editable=true slideshow={"slide_type": ""} -->
Third, World War Two did not lead to any significant changes in terms of the geographical location of the company domiciliation market. A number of holding companies decided to leave Luxembourg in 1939 because of the increasingly uncertain political situation. However, the German occupiers did not interfere with the holding regime, either to use it for their own needs or to abolish it. Yet interventions in the financial system by the occupiers were not without consequences. Most of the 16 banks active in Luxembourg at the time of the German invasion had to cease their operations. Banque Alfred Lévy began to dissolve by the late 1930s. The occupiers were only able to seize the bank’s headquarters and furniture as all the assets had been moved abroad: the main partner, Alfred Lévy, considered Jewish by the Nazi occupiers, had left Luxembourg for the United States. The bank, which had been a major player in domiciliation, would not return to the Luxembourg market after 1944. Another bank, also defined as Jewish by the German occupiers, the Banque Commerciale, survived under trusteeship management (treuhänderischer Verwaltung) throughout the war <cite id="ouet6"><a href="#zotero%7C6915743%2FZANTZ8SS">(Volkmann, 2010)</a></cite>(285) and resumed its activities in the holding market after the liberation. The new regulations imposed on notaries by the occupiers did not prevent them from continuing to offer domiciliation services. However, after the death of Paul Kuborn during the war, only the notary François Altwies continued to provide this service. Although two major players—Kuborn and Banque Lévy—disappeared, the market remained geographically concentrated around Boulevard Royal.

<!-- #endregion -->

<!-- #region editable=true slideshow={"slide_type": ""} -->
## Specialisation and (partial) delocalisation
<!-- #endregion -->

<!-- #region citation-manager={"citations": {"30ii9": [{"id": "6915743/9RDE745W", "source": "zotero"}], "e0r4j": [{"id": "6915743/E2IA8V5V", "source": "zotero"}], "hs8w8": [{"id": "6915743/K3TWJ2VK", "source": "zotero"}], "mlfwk": [{"id": "6915743/SFBR28VT", "source": "zotero"}], "vbk7t": [{"id": "6915743/Q85HJM6U", "source": "zotero"}]}} editable=true slideshow={"slide_type": ""} -->
From the 1960s onwards, data was no longer introduced manually but was processed digitally. Shell companies are no longer identified by their designation as “holding companies” but instead by the concentration of companies at specific addresses. The more companies registered at a single address, the higher the likelihood that they are shell companies. This criterion has been used by the EU Tax Observatory to map shell companies around the world <cite id="mlfwk"><a href="#zotero%7C6915743%2FSFBR28VT">(Aliprandi et al., 2024)</a></cite>. Until the 1980s, the historical centre of Luxembourg City around the Boulevard Royal maintained its centrality. This geographical stability for something that did not need to exist physically—shell companies—is remarkable. “Luxembourg’s Wall Street”, as it was labelled by the Luxembourgish magazine Revue in 1965 <cite id="e0r4j"><a href="#zotero%7C6915743%2FE2IA8V5V">(Duval et al., 2023)</a></cite>(77), only lost its centrality for the shell company market in the 1980s. Shell companies started to be registered outside the traditional spatial boundaries. This expansion extended not only to the often-mentioned Kirchberg district, which became an important service area from the 1960s onwards with the establishment of European institutions and financial service providers, and has already attracted some attention <cite id="hs8w8"><a href="#zotero%7C6915743%2FK3TWJ2VK">(Pesch, 2014)</a></cite><cite id="30ii9"><a href="#zotero%7C6915743%2F9RDE745W">(Pauly, 2018)</a></cite>, but also to Limpertsberg. In the 1980s, the redevelopment of the Glacis plateau drew several banks and financial service providers to the area, at a time when many were advocating for the development of the Glacis, a “wasteland” separating the old town from Limpertsberg, as the site for the rapidly growing financial centre <cite id="vbk7t"><a href="#zotero%7C6915743%2FQ85HJM6U">(Miltgen &#38; Hamilius Jr., 1987)</a></cite>.  
<!-- #endregion -->

<!-- #region citation-manager={"citations": {"jc4j5": [{"id": "6915743/TJW8KC55", "source": "zotero"}]}} editable=true slideshow={"slide_type": ""} -->
A second shift became noticeable in the 2000s. The historical city centre was largely abandoned and new areas were developed, such as Kirchberg, Belair-Limpertsberg and Ban de Gasperich, a new district that has been the focus of a master development plan since 2004 <cite id="jc4j5"><a href="#zotero%7C6915743%2FTJW8KC55">(Hesse, 2013)</a></cite>. In these new areas, the establishment of companies handling domiciliation often serves as a precursor and is considered an indicator of their viability. By the 2010s, this change was firmly established: of the 20 main addresses used by companies in Luxembourg, only three remain in the historical centre of Luxembourg City, while the four most used addresses are now in Gasperich. This geographical shift reflects three key phenomena. 
<!-- #endregion -->

<!-- #region editable=true slideshow={"slide_type": ""} -->
First, there has been a geographical expansion of the financial centre, particularly towards Kirchberg and Ban de Gasperich. The growth in the number of people working there (Fig. 4) meant that it was no longer possible to concentrate all the service providers within the historical centre, which found itself confronted with a very high demand for real estate.
<!-- #endregion -->

```python editable=true slideshow={"slide_type": ""} tags=["figure-employees-*"]
from IPython.display import Image 
metadata={
    "jdh": {
        "module": "object",
        "object": {
            "type":"image",
            "source": [
                "Fig. 4. Evolution of the number of employees in the financial center of Luxembourg."
            ]
        }
    }
}
display(Image("./media/employees-evolution.png"), metadata=metadata)
```

<!-- #region citation-manager={"citations": {"hmlpm": [{"id": "6915743/E8INQQIK", "source": "zotero"}], "z642u": [{"id": "6915743/DQ7RGENX", "source": "zotero"}]}} editable=true slideshow={"slide_type": ""} -->
Second, this expansion indicates a growing diversification in the financial service provider market. In 1999, a law regulated the activity of domiciliation agents for the first time, restricting it to professionals in the financial and insurance sectors, lawyers, auditors and accountants <cite id="hmlpm"><a href="#zotero%7C6915743%2FE8INQQIK">(Ducat, 2012)</a></cite>. It introduced the obligation to know the real identity of the members of the company’s governing bodies. This new regulation is leading to a reorganisation of the domiciliation market, which is gradually being abandoned by banks, lawyers and the Big Four, who are leaving this market to new players or outsourcing it. In 2002, BIL, which has held a central position in domiciliation since the Holding Company Act was adopted in 1929, decided to create a new company, Experta, to manage domiciliation. The new subsidiary completely took over the bank’s Corporate Engineering Department (‘Experta Luxembourg, la nouvelle filiale de Dexia BIL pour développer ses activités d’ingénierie financière’ 2002). The large audit companies did the same, with PWC creating Alter Domus in 2004, and law firms like Arendt & Medernach creating Arendt Services in 2009. The new regulations, as well as the risks, notably reputational, associated with domiciliation, explain this outsourcing of an activity that since the 1930s had been an integral part of the activities of banks, notaries and lawyers <cite id="z642u"><a href="#zotero%7C6915743%2FDQ7RGENX">(Thomas, 2014)</a></cite>. But there are also emerging new players who are arriving in Luxembourg because of the market’s specialisation. In 2004, this specialisation led to the creation of an association aimed at defending the sector’s interests, the Luxembourg International Management Service Association, mainly representing the major players. This process made the market less viable for smaller domiciliation companies. Indeed, while the top 20 most used addresses still included relatively small fiduciaries in the 1980s and 1990s, this was no longer the case from the 2000s onwards. However, unlike the banking sector, lawyers or even audit firms, which became objects of interest in the social sciences in general and history in particular, both internationally and in Luxembourg, domiciliation remains a largely unknown area, even in the media.
<!-- #endregion -->

<!-- #region citation-manager={"citations": {"46kbd": [{"id": "6915743/XXE853S5", "source": "zotero"}], "u40pf": [{"id": "6915743/C6AHEBPR", "source": "zotero"}], "xhsdb": [{"id": "6915743/E2IA8V5V", "source": "zotero"}], "ze32c": [{"id": "6915743/S8ZSA4PT", "source": "zotero"}]}} editable=true slideshow={"slide_type": ""} -->
Third, the peripheralisation of the domiciliation market is also linked to its being considered less prestigious despite its economic significance. In a 2014 study, economist Pierre Mallet estimated that the domiciliation sector employed around 2,600 people and generated 400 million euros in added value (0.9 percent of GDP). The sector is booming, in particular as a result of investment funds. Between 2008 and 2012, the domiciliation business recorded annual growth of over eleven percent. Among the companies listed in 2016 as the main address providers, several rank among the top 50 employers in Luxembourg. However, unlike Chinese banks, which began investing in Luxembourg in the 2000s and primarily established themselves in the historical centre—especially Bank of China, which took over the historic BGL address and now enjoys the best visibility on Boulevard Royal—, this was not the case for domiciliation companies. The marginality of these companies is also reflected in the architecture of their buildings. In contrast to the prominence seen in the construction of banks in Luxembourg from the 1960s <cite id="u40pf"><a href="#zotero%7C6915743%2FC6AHEBPR">(Nottrot &#38; Theis, 2000)</a></cite>;<cite id="xhsdb"><a href="#zotero%7C6915743%2FE2IA8V5V">(Duval et al., 2023)</a></cite>, and later legal practices and large law firms which enlisted renowned architects <cite id="46kbd"><a href="#zotero%7C6915743%2FXXE853S5">(Coubray Céline, 2015)</a></cite>;<cite id="ze32c"><a href="#zotero%7C6915743%2FS8ZSA4PT">(Coubray Céline, 2015b)</a></cite>, domiciliation companies opted for less notable designs.
<!-- #endregion -->

<!-- #region editable=true slideshow={"slide_type": ""} -->
# Global geographies
<!-- #endregion -->

<!-- #region citation-manager={"citations": {"5u32k": [{"id": "6915743/CM9PFR35", "source": "zotero"}], "ldwwb": [{"id": "6915743/MH4PGKJU", "source": "zotero"}]}} editable=true slideshow={"slide_type": ""} -->
Shell companies serve their purpose because they are embedded in larger global tax chains. Most Luxembourg holdings in the interwar period functioned adequately and did not require an additional layer of opacity: they did not yet operate like matryoshka dolls. In the 1930s, a Luxembourg shell company did not yet need shell companies from other countries to offer an effective product. However, several regions known as offshore financial centres were already mentioned in the Luxembourg company register. In general, the holdings market during the interwar period was oriented towards France and Belgium, which accounted for over 50% of the identified holding companies. Following Luxembourg's exit from the German economic area after World War I (the end of the Zollverein, the withdrawal of German capital from the steel and financial sectors, etc.), it became closely tied to the economies of France and Belgium <cite id="5u32k"><a href="#zotero%7C6915743%2FCM9PFR35">(Leboutte et al., 1998)</a></cite>: capital from these two countries took control of the Banque Internationale à Luxembourg. Belgium played a central role through the creation of the Banque Générale du Luxembourg, funded with Belgian money. In the early years of the holdings regime, Germany also held an important position—18% of the holdings identified in 1930 had ties to Germany—, but this percentage dropped significantly after the National Socialists came to power in 1933. Between 1934 and 1939, the percentage of German-linked holdings fell to just 1%. While neighbouring countries with strong economic relations with Luxembourg (France, Belgium, the Netherlands, Germany and the United Kingdom) accounted for about 75% of the market, a country with limited economic ties to Luxembourg, namely Switzerland, began to play an increasingly significant role in the domiciliation landscape, rising from 5% in 1931 to 38% in 1937. By the end of World War I, Switzerland had become one of the most important players in the domiciliation market, offering a fiscally attractive holding regime as well as opportunities for concealment <cite id="ldwwb"><a href="#zotero%7C6915743%2FMH4PGKJU">(Paquier, 2001)</a></cite>. This led to the emergence of more complex fiscal structures involving two offshore financial centres, such as Luxembourgish and Swiss shell companies intertwined to conceal French capital, providing even greater opacity. Other countries offering similar solutions, such as Liechtenstein, Panama and Monaco, were (still) largely absent from the geography of the Luxembourg domiciliation market. After World War II, the two main domiciliation players, BGL and BIL, changed their registration strategies, no longer involving external individuals—a practice used in the 1920s and 1930s to give holdings a “nationality”, making it nearly impossible to identify the real beneficiaries as “national” entities.
<!-- #endregion -->

<!-- #region citation-manager={"citations": {"dyaax": [{"id": "6915743/FM6V699S", "source": "zotero"}]}} editable=true slideshow={"slide_type": ""} -->
To analyse the second data series (1960-2016), we took a different approach from the one used for the first series. To identify the geographies of global tax chains in which Luxembourg is involved, we based our analysis on locations defined as tax havens by James Hines. In 2010, he published a list of 52 “treasure islands” <cite id="dyaax"><a href="#zotero%7C6915743%2FFM6V699S">(Hines Jr, 2010)</a></cite>. We cross-referenced this list (adding Curaçao) with companies linked to these countries to determine Luxembourg’s evolving position in the global geography of domiciliation.
<!-- #endregion -->

<!-- #region jdh={"module": "object", "object": {"source": ["Five most important represented countries in the \u201ctax haven corpus"]}} editable=true slideshow={"slide_type": ""} tags=["table-important-*"] -->
| 1961–69                       | 1970–79                         | 1980–89                      | 1990–99                          | 2000–09                            | 2010–16                        |
|------------------------------|----------------------------------|------------------------------|----------------------------------|------------------------------------|--------------------------------|
| Switzerland - 61.15%         | Switzerland - 64.50%            | Switzerland - 47.71%         | Switzerland - 27.82%             | Switzerland - 19.80%               | Switzerland - 21.66%           |
| Netherlands Antilles - 9.88% | Liechtenstein - 6.87%           | Panama - 13.19%              | Panama - 14.56%                  | British Virgin Islands - 11.49%    | Jersey - 10.41%                |
| Jersey - 5.86%               | Jersey - 4.43%                  | Jersey - 5.37%               | British Virgin Islands - 8.13%   | Panama - 9.62%                     | Cayman Island - 9.76%          |
| Bahamas - 6.45%              | Netherlands - 3.63%             | Hong-Kong - 4.81%            | Ireland - 8.08%                  | Jersey - 8.69%                     | Ireland - 9.04%                |
| Panama - 5.45%               | Panama - 2.86%                  | Lebanon - 4.07%              | Jersey - 5.72%                   | Ireland - 6.36%                    | British Virgin Islands - 5.64% |

<!-- #endregion -->

<!-- #region editable=true slideshow={"slide_type": ""} -->
The data from Table 1 tells two stories. On one hand, it highlights the importance of certain continuities, emphasising the significance of path dependencies established as early as the interwar period. Even though Switzerland's proportion fluctuates significantly over time, it remains the most important country throughout the 50 years covered by this corpus. Swiss banks began investing more heavily in Luxembourg from the 1970s onwards, with the arrival of Union de Banques Suisses (UBS) in 1973 and Société de Banque Suisse (SBS) in 1974. Several Luxembourg banks opened branches in Switzerland: Compagnie Luxembourgeoise de Banque (a subsidiary of Dresdner Bank) since 1972, Kredietbank Luxembourg by acquiring Kredietbank Suisse, initially a subsidiary of KB Belgium established in 1970, since 1980 (with occasional branches in Basel and Lugano) (‘Expansion im Auslandsgeschäft’ 1980), Banque Générale du Luxembourg operated in Zurich from 1982 to 2016, and BIL began in Lausanne (in 1985) and today operates in Geneva, Zurich and Lugano. The Luxembourg market for domiciliation was closely monitored by the Swiss Embassy in Luxembourg. This symbiosis between the two financial centres has existed since the interwar period. Given the wide variety of tax laws in Switzerland, it seemed interesting to present a more detailed view of the geographical links these companies have with different cantons.
<!-- #endregion -->

<!-- #region jdh={"module": "object", "object": {"source": ["Five most represented Swiss cantons among the Swiss corpus (1961-2016)"]}} editable=true slideshow={"slide_type": ""} tags=["table-swiss-*"] -->
| Geneva   | Zurich   | Zug     | Bern    | Ticino  |
|----------|----------|---------|---------|---------|
| 34.81%   | 33.08%   | 12.49%  | 3.91%   | 2.15%   |

<!-- #endregion -->

<!-- #region citation-manager={"citations": {"aibuj": [{"id": "6915743/45A3D99M", "source": "zotero"}], "bmj4g": [{"id": "6915743/M3IBW74Z", "source": "zotero"}], "qhuro": [{"id": "6915743/3B48CIBD", "source": "zotero"}], "x2lsb": [{"id": "6915743/EGTFAR4N", "source": "zotero"}]}} editable=true slideshow={"slide_type": ""} -->
The domiciliation sector in Luxembourg also followed international trends. The presence of the British Virgin Islands (BVI) in the Luxembourgish company register is linked to the rise of the Caribbean territory in this industry. The BVI was a relatively late entrant to the shell company market but quickly assumed a pivotal role. In 1984, the International Business Companies Act created an infrastructure that went beyond the low-level obligations that existed in other shell companies. It did so by eliminating the requirement for boards of directors to meet on tax-haven territory and by exempting investment earnings from income tax <cite id="aibuj"><a href="#zotero%7C6915743%2F45A3D99M">(Maurer, 2000)</a></cite>;<cite id="bmj4g"><a href="#zotero%7C6915743%2FM3IBW74Z">(Campbell, 2021)</a></cite>. The emergence of Ireland in the 1990s reflects the rise of a highly dynamic offshore financial centre. With the creation of Dublin’s International Financial Services Centre (IFSC) in 1987 and the adoption of a highly favourable regulatory framework (such as Section 110 of the Taxes Consolidation Acts in 1997), Ireland quickly became a significant hub for tax planning for multinational companies <cite id="qhuro"><a href="#zotero%7C6915743%2F3B48CIBD">(Murphy, 1998)</a></cite>;<cite id="x2lsb"><a href="#zotero%7C6915743%2FEGTFAR4N">(Allen, 2016)</a></cite>. While Ireland is often portrayed as a competitor to Luxembourg, the domiciliation market also highlights the interdependence and therefore complementarity between the two European countries.
<!-- #endregion -->

<!-- #region citation-manager={"citations": {"dq9hb": [{"id": "6915743/BVAZXXEH", "source": "zotero"}]}} editable=true slideshow={"slide_type": ""} -->
Other offshore financial centres appeared more sporadically. For example, Lebanon’s strong presence was temporary and could partly be attributed to its development as a major financial centre in the Middle East during the 1970s <cite id="dq9hb"><a href="#zotero%7C6915743%2FBVAZXXEH">(Gregory, 1976)</a></cite>, a phenomenon which did not initially seem to be overly disrupted by the outbreak of civil war in 1975. Additionally, the oil shocks of 1973/74 and 1979 created a substantial petrodollar market, with Lebanon and Luxembourg emerging as key nodes: the former as a collection point, and the latter as a conduit for injecting these dollars into international markets. However, the prolonged war in Lebanon (the hostilities did not cease until 1990) eventually led to the decline of Beirut as a financial hub.
<!-- #endregion -->

<!-- #region editable=true slideshow={"slide_type": ""} -->
But this overall global history of the financial centre is very closely intertwined with local networks and professions, as the case studies of the relationship between Luxembourg and two offshore centres, Panama and Niue, show.
<!-- #endregion -->

<!-- #region editable=true slideshow={"slide_type": ""} -->
## Panama, a long standing history
<!-- #endregion -->

<!-- #region citation-manager={"citations": {"c1mlq": [{"id": "6915743/7HJ46WV6", "source": "zotero"}], "x543k": [{"id": "6915743/DP3EGGH6", "source": "zotero"}]}} editable=true slideshow={"slide_type": ""} -->
Panama appeared for the first time in the Luxembourg company register in 1939. The Luxembourg holding company Union Internationale de Placement, whose shareholders were French, was transferred to a Panamanian holding company. Since the construction of the Panama Canal (1904-1914), the young republic had become a hub for financial innovation. In 1927, Panama introduced a new legal framework for companies, partly inspired by Delaware’s legal regime. This new law explicitly provided a favourable environment for offshore companies <cite id="x543k"><a href="#zotero%7C6915743%2FDP3EGGH6">(Barsallo Pérez, 1994)</a></cite>(401). After World War II, although the number of Luxembourg holding companies with ties to Panama was not very high, the Central American country was regularly mentioned in the Luxembourg company register. The most well-known case was the use of Luxembourg by the IOS empire, a Panamanian company, to manage its investment funds in the 1960s, taking advantage of Luxembourg’s light regulation and favourable tax regime **(B. Majerus 2020)**;<cite id="c1mlq"><a href="#zotero%7C6915743%2F7HJ46WV6">(Calabrese, 2023)</a></cite>. From the 1950s onwards, Panama emerged as a direct competitor to Luxembourg. During the budget debates in the Chamber of Deputies in 1955, socialist deputy Adrien van Kauvenbergh identified five countries that should be considered competitors in the field of “favoured holding companies”: Switzerland, Liechtenstein, Tangier in Morocco, Panama and Curaçao. Over the following years, this sentiment persisted. During the discussions initiated in the late 1960s by Michel Debré, the French Minister of Economy and Finance, to harmonise taxation at the European level, a Luxembourg banker was quoted in the February 1968 issue of La Vie française, a French economic weekly, with the following remark when faced with the prospect of reducing Luxembourg’s advantages at the time: “Countries outside the Common Market will benefit—Switzerland, or even Bermuda or Panama. And even the United States, since Delaware is already competing with us.” Pierre Werner reiterated the same reasoning a year later in an article published in November 1969 in the Gazette de Lausanne: “The European Community has no interest in destroying what has been built in Luxembourg for another reason as well: the operations that take place here would happen elsewhere anyway, for example in Panama or the Bahamas, but not within the Community, and would therefore escape its control.” In December 1968, the Belgian daily newspaper L’Echo de l’Industrie published an opinion piece by Professor R. Vandeputte in which he criticised Luxembourg’s position: “It is not healthy (...) that small states like the Grand Duchy or countries of insignificant size, such as Liechtenstein or Panama, owe part of their prosperity to policies that distort the normal application of tax regulations.”
<!-- #endregion -->

```python

```

```python editable=true slideshow={"slide_type": ""} tags=["figure-panama-*"]
from IPython.display import Image 
metadata={
    "jdh": {
        "module": "object",
        "object": {
            "type":"image",
            "source": [
                "Fig. 5. Percentage of companies with a reference to Panama in the treasure island corpus."
            ]
        }
    }
}
display(Image("./media/panama-evolution.png"), metadata=metadata)
```

<!-- #region citation-manager={"citations": {"ktwzl": [{"id": "6915743/876AM7A8", "source": "zotero"}], "okrii": [{"id": "6915743/Q5XAGAAZ", "source": "zotero"}]}} editable=true slideshow={"slide_type": ""} -->
It was from the 1980s onwards that the number and percentage of companies with ties to Panama increased significantly. There are many reasons for this upsurge. While Panama was mainly presented as an offshore centre focused on banking secrecy in the 1970s, ten years later, domiciliation became its main selling point. Starting from the second half of the 1970s, a more liberal political and economic regime was established <cite id="ktwzl"><a href="#zotero%7C6915743%2F876AM7A8">(Ardito-Barletta, 1997)</a></cite>;<cite id="okrii"><a href="#zotero%7C6915743%2FQ5XAGAAZ">(Conniff &#38; Bigler, 2019)</a></cite>. In Luxembourg, domiciliation also emerged as an increasingly important niche from the second half of the 1960s onwards, with significant acceleration in the late 1980s (Fig. 6).
<!-- #endregion -->

```python editable=true slideshow={"slide_type": ""} tags=["figure-holding-*"]
from IPython.display import Image 
metadata={
    "jdh": {
        "module": "object",
        "object": {
            "type":"image",
            "source": [
                "[Figure] Fig. 6. Number of holding companies created in Luxembourg between 1960 and 1988."
            ]
        }
    }
}
display(Image("./media/holdings-evolution.png"), metadata=metadata)
```

<!-- #region citation-manager={"citations": {"1lfqk": [{"id": "6915743/ENUHGCJB", "source": "zotero"}], "qfzvc": [{"id": "6915743/QXSK7DKR", "source": "zotero"}]}} editable=true slideshow={"slide_type": ""} -->
This explains why Panamanian service providers opened branches in Luxembourg. The law firm Mossack Fonseca officially arrived in Luxembourg in 1988, eleven years after it was founded in Panama <cite id="qfzvc"><a href="#zotero%7C6915743%2FQXSK7DKR">(Poujol, 2016)</a></cite>. The notary Marc Elter, who managed Mossack Fonseca’s registration, was one of the notaries specialised on Panama. His father, Prosper-Robert Elter, had already been one of the few notaries handling the domiciliation of companies in the late 1950s. The company “Mossack Fonseca & Co” aimed “to assist individuals and legal entities in the formation and domiciliation of companies”: its office was located at 43 Boulevard Joseph II in a wealthy neighbourhood, just a stone’s throw from the prestigious Luxembourgish law firm Elvinger Hoss Prussen, among others. But by 1988, Mossack Fonseca had already been active in the Luxembourg domiciliation market for seven years. In 1981, Jürgen Mossack, along with two other Panamanian businessmen, took over the administration of Intercommerce Holding, established in 1966, which until then had been managed by KBL front men and belonged to a holding company created in 1954 and owned by Brussels-based companies. A year after Mossack Fonseca’s arrival, Algocal opened an office in Luxembourg, at 13 Boulevard Royal, with the help of the Luxembourgish law firm Bonn & Schmitt. Jaime Alemán, founding partner of Algocal, and Alex Schmitt, the senior partner at Bonn & Schmitt, were not only business partners but also maintained a personal relationship—for instance, Alex Schmitt and his wife attended the wedding of Jaime Alemán’s daughter <cite id="1lfqk"><a href="#zotero%7C6915743%2FENUHGCJB">(Aleman Healy, 2014)</a></cite>(643).
<!-- #endregion -->

<!-- #region editable=true slideshow={"slide_type": ""} -->
Mossack Fonseca and Algocal were two relatively young law firms that were not related to historical Panamanian firms such as Arifa (est. 1914), IGRA (est. 1920) and Morgan & Morgan (est. 1923). Founded in 1977 and 1985 respectively, they represented a new generation of Panamanian lawyers. Among the historical firms, only Arifa opened a branch in Luxembourg in 1993, with two Panamanian lawyers as directors and Evelyne Jastrow as their representative in Luxembourg.
<!-- #endregion -->

<!-- #region citation-manager={"citations": {"ou8vs": [{"id": "6915743/RZ3ZVKZU", "source": "zotero"}]}} editable=true slideshow={"slide_type": ""} -->
The list of figures named in the Panama Papers <cite id="ou8vs"><a href="#zotero%7C6915743%2FRZ3ZVKZU">(Raizer, 2016)</a></cite> was highly biased because the investigation was limited to the study of Mossack Fonseca, which was indeed specialised in the domiciliation market but did not necessarily have a good reputation. Other major law firms were also present. Morgan & Morgan was represented in Luxembourg by lawyer Patrick Houbert and Algocal by Alain Schmitt and also by the fiduciary Lex Benoy.
<!-- #endregion -->

<!-- #region editable=true slideshow={"slide_type": ""} -->
The longitudinal study made possible by the Luxembourg company register offers a more complex and detailed image. Two groups of professions stand out—two groups that have so far scarcely appeared in the history of the Luxembourg financial centre or the history of global tax chains: notaries and fiduciaries.
<!-- #endregion -->

<!-- #region citation-manager={"citations": {"2koef": [{"id": "6915743/G4EZ5HMX", "source": "zotero"}], "719ga": [{"id": "6915743/9ASG5329", "source": "zotero"}], "ytria": [{"id": "6915743/P5PK22GD", "source": "zotero"}]}} editable=true slideshow={"slide_type": ""} -->
In Luxembourg, the profession of notary is highly regulated, with the number of notaries in the country set by law. Often presenting themselves as mere authenticators of deeds, they play a much more central role in the domiciliation industry. Through the case study of Panama, it becomes apparent that some notaries specialise in the domiciliation of companies. Two notaries in Luxembourg are implicated in the creation of almost a quarter of the companies with links to Panama: Joseph Elvinger and Jean Seckler. The former, close to the liberal-leaning Luxembourg Democratic Party—in his youth, he was the deputy leader of the party’s youth wing JDL (‘Ils dirigent la JDL’ 1977)—, has close links with the prestigious Luxembourgish law company Elvinger Hoss & Prussen: André Elvinger, one of the founders of EHP, affectionately referred to him as “our notary” <cite id="ytria"><a href="#zotero%7C6915743%2FP5PK22GD">(Elvinger, André, 2017)</a></cite>(7). In 1998, Joseph Elvinger took over a notarial practice that had been in the domiciliation market since the interwar period. Tony Neuman was one of the four main notaries for the creation of holdings during the interwar period <cite id="719ga"><a href="#zotero%7C6915743%2F9ASG5329">(Calabrese &#38; Majerus, 2024)</a></cite>. Neuman’s successor, Charles Michels, was less active in this area, but his successor, Camille Hellinckx, dominated the market from the 1970s to the 1990s before Joseph Elvinger took over the practice from 1998 to 2014—undoubtedly benefiting from the knowledge, networks and techniques of his predecessors. Less is known about Jean Seckler, the second important notary, except that he was very well connected in financial networks. When a Luxembourg investment bank, Compagnie de Banque Privée Luxembourg, was established in 2006, Jean Seckler was among those involved, alongside Bob Bernard and Norbert Becker, the former managing partner of Arthur Andersen <cite id="2koef"><a href="#zotero%7C6915743%2FG4EZ5HMX">(Poujol, 2006)</a></cite>.
<!-- #endregion -->

<!-- #region citation-manager={"citations": {"pfw3i": [{"id": "6915743/ENSWA9Z4", "source": "zotero"}]}} editable=true slideshow={"slide_type": ""} -->
The second key players are fiduciary companies. Some larger Luxembourgish companies were incorporated into larger international groups when what would become the “Big Four” established themselves in Luxembourg: Fiduciaire Générale du Luxembourg joined Touche, which later became Deloitte; Compagnie Fiduciaire joined Arthur Young; Interfiduciaire joined KMG; and PriceWater Fiduciaire joined Victor Steichen. However, other small fiduciaries continued to survive, particularly around the domiciliation market **(Majerus, forthcoming)**. Regarding Panama, Fiducenter stands out as an essential player. It was created in 1980 through the partnership of a Luxembourgish accountant, a Luxembourgish broker, and a Swiss fiduciary from the canton of Gsteig. Following the introduction of the law on domiciliation in 1999, Fiducenter was one of the first companies to receive the now necessary accreditation to continue in this market <cite id="pfw3i"><a href="#zotero%7C6915743%2FENSWA9Z4">(“Dix Professionnels Agréés,” 2000)</a></cite>. It opened offices in Cyprus in 2004, in Singapore in 2011, and in Malta. In 2013, it partnered with Oak, a service provider based in another centre specialising in domiciliation, Guernsey. Fiducenter offered near complete opacity: the companies it created were entirely staffed by people working at Fiducenter, thus providing no indication of the real beneficiaries of these offshore companies. Fiducenter worked closely with the two notaries most involved in the Panama market. The scandal surrounding the Panama Papers was not necessarily seen as a problem, as it allowed the market to be redirected, notably towards Cyprus, as explained by the head of the Cypriot office of Fiducenter in 2016. Below Fiducenter, there were a small number of lesser-known fiduciaries that carried out the essential task of concealing company structures by using Panamanian companies. These included Fidei Fiduciaire, founded in 1993 by the Belgian Bruno Beernaerts, and Fiduciaire Fernand Faber, established in 1952 and whose founder, Fernand Faber, had been President of the Order of Chartered Accountants of Luxembourg in the 1970s.
<!-- #endregion -->

<!-- #region editable=true slideshow={"slide_type": ""} -->
## Niue, a short-living blip
<!-- #endregion -->

<!-- #region editable=true slideshow={"slide_type": ""} -->
Niue is a small country in the South Pacific Ocean, with a land area of 261.46km² and a population of around 1,600 inhabitants. It is closely associated with New Zealand, which handles several state functions on its behalf. Recently, Niue has made headlines as global warming directly threatens its existence, with rising sea levels jeopardising the island’s physical viability. The tourist office presents the island as “a place where it’s normal for complete strangers to wave at each other, all the time. It’s a place where nature hasn’t been broken… and things are ‘the way they used to be’”(‘The Official Website Of Niue Tourism’, n.d.). For a short time, this island appeared in the Luxembourg company register, and for two years it was one of the six main “treasure islands” for Luxembourgish offshore companies (Table 3).
<!-- #endregion -->

<!-- #region editable=true slideshow={"slide_type": ""} tags=["table-niue-*"] -->
Table 3 - Percentage of the treasure island corpus of companies with a reference to Niue.

| 1995 | 1996 | 1997 | 1998 | 1999 | 2000 | 2001 | 2002 | 2003 | 2004 | 2005 | 2006 |
|------|------|------|------|------|------|------|------|------|------|------|------|
| 0%   | 0.59%| 0.82%| 3.38%| 4.20%| 4.78%| 4.79%| 2.35%| 1.46%| 1.49%| 1.31%| 0.68% |

<!-- #endregion -->

<!-- #region citation-manager={"citations": {"e711k": [{"id": "6915743/G4ABR2SI", "source": "zotero"}], "hv6aq": [{"id": "6915743/2MKD44DI", "source": "zotero"}]}} editable=true slideshow={"slide_type": ""} -->
The reasons for this sudden surge are related to Panama, another offshore financial centre with links to Luxembourg, as described above. It was in the early 1990s that the idea emerged within Panamanian business circles to use this island as a domiciliation space. The Niuean government was persuaded to offer this new service. It was the Panamanian law firm Mossack Fonseca that drafted the legislative framework, inspired by the framework used in the British Virgin Islands. Niue offered the advantage of avoiding the reputation issues that could arise from having a company domiciled in Panama. At the same time, having offices in a time zone suitable for the Asian market, particularly China and Russia, also proved to be advantageous <cite id="e711k"><a href="#zotero%7C6915743%2FG4ABR2SI">(Chambost, 1999)</a></cite>;<cite id="hv6aq"><a href="#zotero%7C6915743%2F2MKD44DI">(Fischer, 2023)</a></cite>(197).
<!-- #endregion -->

<!-- #region citation-manager={"citations": {"2rtkt": [{"id": "6915743/EB38VNIX", "source": "zotero"}], "ubha8": [{"id": "6915743/EB38VNIX", "source": "zotero"}], "vraco": [{"id": "6915743/TCFHRQN9", "source": "zotero"}]}} editable=true slideshow={"slide_type": ""} -->
Mossack Fonseca secured a 20-year monopoly for the domiciliation of companies, adopting a model of foreign professional monopoly agencies which had also been tried in other micro-states <cite id="2rtkt"><a href="#zotero%7C6915743%2FEB38VNIX">(Van Fossen, 2012)</a></cite>. For a short time, this policy bore fruit: for three years, 10% of the Niuean government’s revenue came from OFC fees. But the island of Niue soon began to appear on tax haven lists. As early as 2001, JP Morgan Chase Bank, among others, decided to stop using Niue. The pressure from international organisations was such that by 2002, the Niuean government had committed to a policy aimed at limiting offshore legislation <cite id="ubha8"><a href="#zotero%7C6915743%2FEB38VNIX">(Van Fossen, 2012)</a></cite>. Following this decision, Mossack Fonseca decided to shift its domiciliation market to the neighbouring island of Samoa <cite id="vraco"><a href="#zotero%7C6915743%2FTCFHRQN9">(Findley et al., 2014)</a></cite>(41). The events in Niue directly impacted the Luxembourg domiciliation market because of the Panamanian connection linking Niue and Luxembourg. As shown in the previous section, several Panamanian law firms had established a presence in Luxembourg, including Mossack Fonseca, which had even opened an office in Luxembourg.
<!-- #endregion -->

<!-- #region editable=true slideshow={"slide_type": ""} -->
The relatively small number of companies linked to Niue and Niue’s brief presence in the incorporation market offer the opportunity of a microhistory of domiciliation. Far from the large business law firms and international audit companies, we discover an almost invisible microcosm. Of course, there are notaries involved, with two particularly specialised in Niue: Norbert Muller (weighted degree of 1387, highest) and Gérard Lecuit (weighted degree of 503, fifth highest). Both appear regularly in the incorporation market without being among its most prominent figures. Around these two men are several women: Brigitte Siret (weighted degree of 487, sixth highest) and Sandra Vommaro with Norbert Muller, and Angela Palemburgi with Gérard Lecuit. It is not clear from the Mémorial C whether these women work directly for the two notaries, but they belong to a group of individuals, often women, who perform essential tasks of representation and concealment while occupying the lowest rung of the social ladder in the financial sector. They do not appear in specialised press like Paperjam or Agefi, and are rarely present on LinkedIn. Despite this invisibility, they play an essential role in the domiciliation market (see the profile of Leticia Montoya, who served as a sham director for at least 3,200 shell companies in the financial sector). Mossack Fonseca: (Brinkmann, Obermaier, and Obermayer 2016)). A second group of people consists of men who seem to work more or less independently: François David (weighted degree of 503, fourth highest), listed as an “accountant” in the Mémorial C but for whom no other information has been found; Jérôme Guez, listed as a “financial director” in the Mémorial C, who states on X that he worked for “15 years as a fiduciary in Luxembourg”; and Jean-Marie Detourbet, listed as a “manager” in the Mémorial C. These figures, all of Belgian or French nationality, were not deeply enough involved in the Luxembourg domiciliation market to leave more explicit traces there. Closely linked to these apporteurs d’affaires, as they are labelled in French, were fiduciaries and other financial service providers. For Niue, these were relatively small institutions such as LWM Corporate Services, linked to SEB Bank, a Swedish bank; Edmond Rothschild Bank; Luxfudicia, a fiduciary that employed five people in 2015; or Capitole Management Services, a domiciliation provider that went bankrupt in 2002. And finally the incorporation market also needs the intervention of lawyers. Three law firms are particularly represented: the Penning firm (Philippe (weighted degree of 121, 19th highest) and Jim Penning), Chateaux Avocats (Jean-Pascal Cambier) and Lex Thielen (Lex Thielen, Philippe Stroesser).
<!-- #endregion -->

<!-- #region editable=true slideshow={"slide_type": ""} -->
These are small firms, with the first not specialising in domiciliation, unlike the other two. While the names of Jürgen Mossack and Ramos Fonseca do not appear, there is a multitude of sham directors linked to the network of these two lawyers, either in the British Virgin Islands, where they moved part of their domiciliation market, or in Panama (Leticia Montoya (weighted degree of 1309, second highest), Juan Mashburn, Catalina Greenlaw, Darlene Bayne, etc.).
<!-- #endregion -->

<!-- #region citation-manager={"citations": {"lauxn": [{"id": "6915743/WXZKUNFV", "source": "zotero"}]}} editable=true slideshow={"slide_type": ""} -->
In the mid-2000s, a trial in France revealed the profile of the beneficiaries of these structures. In 2001, the company LX Partners was created before the notary Norbert Muller, owned by a company in Gibraltar and a company in Niue and represented by a man named Detourbet. In reality, LX Partners was a family of entrepreneurs from Metz trying to evade French VAT <cite id="lauxn"><a href="#zotero%7C6915743%2FWXZKUNFV">(Poujol, 2014)</a></cite>. Two rulings, one by the Court of Appeal on 15 March 2004 and another by the Administrative Tribunal on 1 February 2018, on the failure to transmit information to Belgian and French tax authorities, also indicate that in the 2000s, these arrangements involved people from Luxembourg’s neighbour countries.
<!-- #endregion -->

<!-- #region editable=true slideshow={"slide_type": ""} -->
The Niuean case is revealing on two levels. On the one hand, it shows the multiplicity of actors involved in making this system work between Luxembourg and a Pacific island—including notaries, sham directors in Luxembourg, the British Virgin Islands and Panama, as well as banks, fiduciary companies and lawyers. But on the other hand, these are figures who appear neither in the history of Luxembourg’s financial centre nor in the global histories of capitalism in the 20th century
<!-- #endregion -->

<!-- #region editable=true slideshow={"slide_type": ""} -->
# Conclusion
<!-- #endregion -->

<!-- #region citation-manager={"citations": {"n5yon": [{"id": "6915743/C6NV55UR", "source": "zotero"}]}} editable=true slideshow={"slide_type": ""} -->
Shell companies are a core function of Luxembourg’s offshore financial sector. This activity can be traced back to the 1930s. It remains important today, as evidenced by the reactions of Luxembourg’s economic and political elites when the Unshell Directive was announced <cite id="n5yon"><a href="#zotero%7C6915743%2FC6NV55UR">(Klein, 2022)</a></cite>. This article attempts an initial mapping of this phenomenon by examining it at two different scales. Starting from the Luxembourgish addresses of shell companies, several phenomena emerge: the geographical dispersion of the financial hub, from the hypercentre around Boulevard Royal in the 1930s to a multi-centre financial hub, though still concentrated in and around Luxembourg City, in the 2010s. These addresses also reflect changes in the actors involved in domiciliation: it was initially a market dominated by banks, before transitioning to other service providers.
<!-- #endregion -->

<!-- #region editable=true slideshow={"slide_type": ""} -->
By positioning the Luxembourg domiciliation market within a global geography, certain geographical chronologies emerge. One is the central role of Switzerland for Luxembourg throughout the 20th century. The extreme responsiveness of the market to changes in capital coding is also evident: ten years after the International Business Companies Act, 12% of companies linked to tax havens were associated with the British Virgin Islands (BVI). At a time when communication had not yet been accelerated by the Internet, this implies a rapid spread of practices and the swift emergence of networks. These transfer processes remain largely underexplored in this paper and will require further research, likely using additional sources.
<!-- #endregion -->

<!-- #region citation-manager={"citations": {"bq0kl": [{"id": "6915743/6BHCQ38V", "source": "zotero"}], "wdp3q": [{"id": "6915743/3PEIJWRJ", "source": "zotero"}]}} editable=true slideshow={"slide_type": ""} -->
By investigating the intersection of these two scales, we can connect two mailboxes: one located at 16 Rue des Capucins, in the very centre of Luxembourg City, the capital of a small state in the European Union, and P.O. Box 71 at 2 Centre Commercial Square in Alofi, the capital of a small island country in the South Pacific Ocean. Despite the one-sided perspective imposed by the choice to use solely Luxembourgish sources, this focus highlights the importance of a localised infrastructure that has been largely overlooked by both Luxembourgish and international historiography: without these numerous “hidden helpers”, there would be no offshore financial centres <cite id="wdp3q"><a href="#zotero%7C6915743%2F3PEIJWRJ">(Derix, 2015)</a></cite>;<cite id="bq0kl"><a href="#zotero%7C6915743%2F6BHCQ38V">(N. Majerus, 1949)</a></cite>.
<!-- #endregion -->

<!-- #region editable=true slideshow={"slide_type": ""} -->
# Bibliography
<!-- #endregion -->

<!-- BIBLIOGRAPHY START -->
<div class="csl-bib-body">
  <div class="csl-entry"><i id="zotero|6915743/ENUHGCJB"></i>Aleman Healy, J. (2014). <i>La Honestidad No Tiene Precio</i>.</div>
  <div class="csl-entry"><i id="zotero|6915743/SFBR28VT"></i>Aliprandi, G., Busschots, T., &#38; Oliveira, C. (2024). <i>Finding shell companies: mapping the global geography of shell companies</i>.</div>
  <div class="csl-entry"><i id="zotero|6915743/EGTFAR4N"></i>Allen, K. (2016). Into the limelight: tax haven Ireland. <i>Irish Marxist Review</i>, <i>5</i>(16), 14–27. <a href="https://www.academia.edu/download/90682249/205.pdf">https://www.academia.edu/download/90682249/205.pdf</a></div>
  <div class="csl-entry"><i id="zotero|6915743/6MGDHU8G"></i>Anders, J. (1928). <i>Essai sur l’évolution bancaire dans le Grand-Duché de Luxembourg: étude historique et économique</i>. Editions Luxembourgeoises.</div>
  <div class="csl-entry"><i id="zotero|6915743/876AM7A8"></i>Ardito-Barletta, N. (1997). The Political and Economic Transition of Panama, 1978–1991. In Dominguez, Jorge &#38; M. Lindenberg (Eds.), <i>Democratic Transitions in Central America</i> (pp. 32–66). University of Florida Press.</div>
  <div class="csl-entry"><i id="zotero|6915743/DP3EGGH6"></i>Barsallo Pérez, C. A. (1994). <i>El secreto bancario en Panamá y España: un estudio comparativo</i>. Universidad Complutense de Madrid. Facultad de Derecho. Departamento de Derecho Mercantil.</div>
  <div class="csl-entry"><i id="zotero|6915743/GJCWQT36"></i>Beckett, P. R. (2023). <i>An Anatomy of Tax Havens: Europe, the Caribbean and the United States of America</i>. De Gruyter. <a href="https://www.degruyter.com/document/doi/10.1515/9783110985108/html">https://www.degruyter.com/document/doi/10.1515/9783110985108/html</a></div>
  <div class="csl-entry"><i id="zotero|6915743/9NP9K8Z4"></i>Bitiukova, N. (2023). The GDPR’s Journalistic Exemption and its Side Effects: GDPR anniversary – what does it mean for the media? <i>Verfassungsblog</i>. <a href="https://verfassungsblog.de/the-gdprs-journalistic-exemption-and-its-side-effects/">https://verfassungsblog.de/the-gdprs-journalistic-exemption-and-its-side-effects/</a></div>
  <div class="csl-entry"><i id="zotero|6915743/JVF2GSFJ"></i>Bourbaki, R. (2016). End of Paradise ? Le Luxembourg et son secret bancaire dans les filets du multilatéralisme. <i>Critique internationale</i>, <i>71</i>(2), 55–71. <a href="https://doi.org/10.3917/crii.071.0055">https://doi.org/10.3917/crii.071.0055</a></div>
  <div class="csl-entry"><i id="zotero|6915743/7HJ46WV6"></i>Calabrese, M. (2023). <i>The Fund Code. A History of Investment Funds in Luxembourg from the Holding Act to the UCITS Legislation (1929-1989)</i> [PhD]. University of Luxembourg,.</div>
  <div class="csl-entry"><i id="zotero|6915743/9ASG5329"></i>Calabrese, M., &#38; Majerus, B. (2024). Archaeology of a Treasure Island: Actors and Practices of Holding Companies in Luxembourg (1929–1940). <i>Contemporary European History</i>, <i>33</i>, 1398–1415. <a href="https://doi.org/10.1017/S0960777323000437">https://doi.org/10.1017/S0960777323000437</a></div>
  <div class="csl-entry"><i id="zotero|6915743/M3IBW74Z"></i>Campbell, A. M. (2021). <i>Money Laundering, Terrorist Financing, and Tax Evasion The Consequences of International Policy Initiatives on Financial Centres in the Caribbean Region</i>. Palgrave.</div>
  <div class="csl-entry"><i id="zotero|6915743/G4ABR2SI"></i>Chambost, É. (1999). <i>Guide Chambost des paradis fiscaux</i> (7th ed.). Favre.</div>
  <div class="csl-entry"><i id="zotero|6915743/Q5XAGAAZ"></i>Conniff, M. L., &#38; Bigler, G. E. (2019). <i>Modern Panama: from occupation to crossroads of the Americas</i>. Cambridge University Press.</div>
  <div class="csl-entry"><i id="zotero|6915743/S8ZSA4PT"></i>Coubray Céline. (2015a). KPMG par Valentiny inauguré au Kirchberg. <i>Paperjam</i>. <a href="https://paperjam.lu/article/news-kpmg-par-valentiny-inaugure-au-kirchberg">https://paperjam.lu/article/news-kpmg-par-valentiny-inaugure-au-kirchberg</a></div>
  <div class="csl-entry"><i id="zotero|6915743/XXE853S5"></i>Coubray Céline. (2015b). Tous sous le même toit. <i>Paperjam</i>. <a href="https://paperjam.lu/article/news-tous-sous-le-meme-toit">https://paperjam.lu/article/news-tous-sous-le-meme-toit</a></div>
  <div class="csl-entry"><i id="zotero|6915743/99Z4RH8W"></i>Davis, N. (2009). Tax spotlight worries Cayman Islands. <i>BBC - News</i>. <a href="http://news.bbc.co.uk/2/hi/americas/7972695.stm">http://news.bbc.co.uk/2/hi/americas/7972695.stm</a></div>
  <div class="csl-entry"><i id="zotero|6915743/3PEIJWRJ"></i>Derix, S. (2015). Hidden Helpers: Biographical Insights into Early and Mid-Twentieth Century Legal and Financial Advisors. <i>European History Yearbook</i>, <i>16</i>, 47–62.</div>
  <div class="csl-entry"><i id="zotero|6915743/ENSWA9Z4"></i>Dix professionnels agréés. (2000). <i>Agefi</i>. <a href="https://www.agefi.lu/Mensuel-Article.aspx?date=Dec-2000&#38;mens=65&#38;rubr=506&#38;art=5271&#38;query=fiducenter">https://www.agefi.lu/Mensuel-Article.aspx?date=Dec-2000&#38;mens=65&#38;rubr=506&#38;art=5271&#38;query=fiducenter</a></div>
  <div class="csl-entry"><i id="zotero|6915743/PQHTQ4XU"></i>Dörry, S. (2016). The role of elites in the co-evolution of international financial markets and financial centres: The case of Luxembourg. <i>Competition &#38; Change</i>, <i>20</i>(1), 21–36.</div>
  <div class="csl-entry"><i id="zotero|6915743/E8INQQIK"></i>Ducat, A. (2012). Avec domicile reconnu. <i>Paperjam</i>, 98–102.</div>
  <div class="csl-entry"><i id="zotero|6915743/E2IA8V5V"></i>Duval, C., Gabellini, M., &#38; Mouton, V. (2023). La BGL, l’architecture d’un siège dans une ville en mutation. <i>Hémecht</i>, <i>75</i>(1), 49–79.</div>
  <div class="csl-entry"><i id="zotero|6915743/P5PK22GD"></i>Elvinger, André. (2017). <i>Hommage à notre pionnier: Paul Elvinger</i>.</div>
  <div class="csl-entry"><i id="zotero|6915743/PCWSS248"></i>Farquet, C. (2010). Expertise et négociations fiscales à la Société des Nations (1923-1939): <i>Relations Internationales</i>, <i>n° 142</i>(2), 5–21. <a href="https://doi.org/10.3917/ri.142.0005">https://doi.org/10.3917/ri.142.0005</a></div>
  <div class="csl-entry"><i id="zotero|6915743/TCFHRQN9"></i>Findley, M. G., Nielson, D. L., &#38; Sharman, J. C. (2014). <i>Global shell games: Experiments in transnational relations, crime, and terrorism</i>. CUP. <a href="https://books.google.com/books?hl=en&#38;lr=&#38;id=DExkAgAAQBAJ&#38;oi=fnd&#38;pg=PR10&#38;dq=,+Global+Shell+Games:+Experiments+in+Transnational+Relations,+Crime+and+Terrorism+&#38;ots=gvhahZ30Qy&#38;sig=c01ddayU1iTMP8-i0VTTJuHpqDY">https://books.google.com/books?hl=en&#38;lr=&#38;id=DExkAgAAQBAJ&#38;oi=fnd&#38;pg=PR10&#38;dq=,+Global+Shell+Games:+Experiments+in+Transnational+Relations,+Crime+and+Terrorism+&#38;ots=gvhahZ30Qy&#38;sig=c01ddayU1iTMP8-i0VTTJuHpqDY</a></div>
  <div class="csl-entry"><i id="zotero|6915743/2MKD44DI"></i>Fischer, H.-D. (2023). <i>100 Years of Pulitzer Prize Reporting on World Economy: From Germany’s Fiscal War Burden in 1916 until the Global Scene of Offshore Companies in 2016</i>. LIT Verlag Münster.</div>
  <div class="csl-entry"><i id="zotero|6915743/BM2KP27N"></i>Friedewald, M. (forthcoming). Access to Public Archives in Europe: Progress in the implementation of CoE Recommendation R (2000)13 on a European policy on access to archives. In <i>Archives and Records</i>. Taylor &#38; Francis.</div>
  <div class="csl-entry"><i id="zotero|6915743/BVAZXXEH"></i>Gregory, P. (1976). La place financière de Beyrouth. <i>Revue d’économie Politique</i>, <i>86</i>(2), 173–194. <a href="https://www.jstor.org/stable/24696781">https://www.jstor.org/stable/24696781</a></div>
  <div class="csl-entry"><i id="zotero|6915743/VU5ZX59D"></i>Guex, S. (2022). The Emergence of the Swiss Tax Haven, 1816–1914. <i>Business History Review</i>, <i>96</i>(2), 353–372. <a href="https://doi.org/10.1017/S0007680520000914">https://doi.org/10.1017/S0007680520000914</a></div>
  <div class="csl-entry"><i id="zotero|6915743/TJW8KC55"></i>Hesse, M. (2013). Das «Kirchberg-Syndrom»: grosse Projekte im kleinen Land: <i>Bauen und Planen in Luxemburg</i>. <i>disP - The Planning Review</i>, <i>49</i>(1), 14–28. <a href="https://doi.org/10.1080/02513625.2013.799854">https://doi.org/10.1080/02513625.2013.799854</a></div>
  <div class="csl-entry"><i id="zotero|6915743/NHPDT9TF"></i>Hesse, M., &#38; Wong, C. (2019). Cities seen through a relational lens. <i>Geographische Zeitschrift</i>. <a href="https://doi.org/10.25162/gz-2019-0020">https://doi.org/10.25162/gz-2019-0020</a></div>
  <div class="csl-entry"><i id="zotero|6915743/FM6V699S"></i>Hines Jr, J. R. (2010). Treasure islands. <i>Journal of Economic Perspectives</i>, <i>24</i>(4), 103–126.</div>
  <div class="csl-entry"><i id="zotero|6915743/E738G59W"></i>Hoffstaetter, S. (2025). pytesseract. <i>GitHub Repository</i>. <a href="https://github.com/ madmaze/pytesseract">https://github.com/ madmaze/pytesseract</a></div>
  <div class="csl-entry"><i id="zotero|6915743/ZIHW85VR"></i>Jahnel, D. (2023). Historisches Arbeiten und Datenschutzrecht. In <i>Digital Humanities in den Geschichtswissenschaften</i> (pp. 562–579). Böhlau Verlag. <a href="https://elibrary.utb.de/doi/10.36198/9783838561165-562-579">https://elibrary.utb.de/doi/10.36198/9783838561165-562-579</a></div>
  <div class="csl-entry"><i id="zotero|6915743/C6NV55UR"></i>Klein, T. (2022). Der Kampf gegen Briefkastenfirmen könnte Luxemburg hart treffen. <i>Luxemburger Wort</i>. <a href="https://www.wort.lu/wirtschaft/der-kampf-gegen-briefkastenfirmen-koennte-luxemburg-hart-treffen/1145974.html">https://www.wort.lu/wirtschaft/der-kampf-gegen-briefkastenfirmen-koennte-luxemburg-hart-treffen/1145974.html</a></div>
  <div class="csl-entry"><i id="zotero|6915743/CM9PFR35"></i>Leboutte, R., Puissant, J., &#38; Scuto, D. (1998). <i>Un siècle d’histoire industrielle, (1873 - 1973), Belgique, Luxembourg, Pays-Bas : industrialisation et sociétés</i>. SEDES.</div>
  <div class="csl-entry"><i id="zotero|6915743/H9ZKDADQ"></i>Luyten, D. (2022). <i>Report on impact of GDPR</i> (European Holocaust Research Infrastructure H2020-INFRAIA-2019-1).</div>
  <div class="csl-entry"><i id="zotero|6915743/6BHCQ38V"></i>Majerus, B., &#38; Zenner, B. (2020). Too small to be of interest, too large to grasp? Histories of the Luxembourg financial centre. <i>European Review of History</i>, <i>27</i>(4), 548–562. <a href="https://doi.org/10.1080/13507486.2020.1751587">https://doi.org/10.1080/13507486.2020.1751587</a></div>
  <div class="csl-entry"><i id="zotero|6915743/M3M2TDWJ"></i>Majerus, N. (1949). <i>Histoire du droit dans le Grand-Duché de Luxembourg</i> (Vol. 2). Imprimerie Saint-Paul.</div>
  <div class="csl-entry"><i id="zotero|6915743/9UCXNVVN"></i><i>Maurer - 2000 - Recharting the Caribbean land, law, and citizensh.pdf</i>. (n.d.).</div>
  <div class="csl-entry"><i id="zotero|6915743/45A3D99M"></i>Maurer, B. (2000). <i>Recharting the Caribbean: land, law, and citizenship in the British Virgin Islands</i>. University of Michigan Press.</div>
  <div class="csl-entry"><i id="zotero|6915743/Q85HJM6U"></i>Miltgen, D., &#38; Hamilius Jr., J. (1987). Auf ewig eine Öde. <i>D’Lëtzebuerger Land</i>, <i>37</i>, 13.</div>
  <div class="csl-entry"><i id="zotero|6915743/3B48CIBD"></i>Murphy, L. (1998). Financial engine or glorified back office? Dublin’s International Financial Services Centre going global. <i>Area</i>, <i>30</i>(2), 157–165. <a href="https://doi.org/10.1111/j.1475-4762.1998.tb00059.x">https://doi.org/10.1111/j.1475-4762.1998.tb00059.x</a></div>
  <div class="csl-entry"><i id="zotero|6915743/C6AHEBPR"></i>Nottrot, I., &#38; Theis, M. (2000). <i>Luxembourg: banks and architecture = banques et architecture = Banken und Architektur</i>. G. Binsfeld.</div>
  <div class="csl-entry"><i id="zotero|6915743/MH4PGKJU"></i>Paquier, S. (2001). Swiss holding companies from the mid-nineteenth century to the early 1930s: the forerunners and subsequent waves of creations. <i>Financial History Review</i>, <i>8</i>(2), 163–182.</div>
  <div class="csl-entry"><i id="zotero|6915743/9RDE745W"></i>Pauly, M. (2018). Luxembourg et Kirchberg: ville médiévale et capitale européenne. In J.-L. Fray (Ed.), <i>Urban Spaces and the complexity of Cities</i>. Böhlau. <a href="https://orbilu.uni.lu/handle/10993/35260">https://orbilu.uni.lu/handle/10993/35260</a></div>
  <div class="csl-entry"><i id="zotero|6915743/K3TWJ2VK"></i>Pesch, F. (2014). <i>Le Fonds d’urbanisation et d’aménagement du plateau de Kirchberg (FUAK). Histoire d’un mal-aimé.</i> Éditions le Phare.</div>
  <div class="csl-entry"><i id="zotero|6915743/DNV4AN63"></i><i>Philippart - 2006 - Luxembourg, de l’historicisme au modernisme. De la ville forteressse à la capitale nationale.pdf</i>. (n.d.).</div>
  <div class="csl-entry"><i id="zotero|6915743/HVMKF47G"></i>Philippart, R. L. (2006). <i>Luxembourg, de l’historicisme au modernisme. De la ville forteressse à la capitale nationale</i> (Vol. 2). Editions Ilôts.</div>
  <div class="csl-entry"><i id="zotero|6915743/G4EZ5HMX"></i>Poujol, V. (2006). Double lion rouge. <i>D’Lëtzebuerger Land</i>, 9. <a href="https://viewer.eluxemburgensia.lu/ark:70795/k1ph31/pages/9/articles/DTL298">https://viewer.eluxemburgensia.lu/ark:70795/k1ph31/pages/9/articles/DTL298</a></div>
  <div class="csl-entry"><i id="zotero|6915743/WXZKUNFV"></i>Poujol, V. (2014). La chasse aux fraudeurs. <i>Paperjam</i>.</div>
  <div class="csl-entry"><i id="zotero|6915743/QXSK7DKR"></i>Poujol, V. (2016). Quand Mossack Fonseca dénonçait la fraude fiscale au Luxembourg. <i>Paperjam</i>. <a href="https://paperjam.lu/article/news-quand-mossack-fonseca-denoncait-la-fraude-fiscale-au-luxembourg">https://paperjam.lu/article/news-quand-mossack-fonseca-denoncait-la-fraude-fiscale-au-luxembourg</a></div>
  <div class="csl-entry"><i id="zotero|6915743/RZ3ZVKZU"></i>Raizer, T. (2016). Panama Papers: à l’ombre de l’offshore mondiale. <i>Paperjam</i>. <a href="https://paperjam.lu/article/news-panama-papers-a-lombre-de-loffshore-mondiale">https://paperjam.lu/article/news-panama-papers-a-lombre-de-loffshore-mondiale</a></div>
  <div class="csl-entry"><i id="zotero|6915743/IBNZ2AD7"></i>Singer-Vine, J., &#38; Jain, S. (2025). pdfplumber. <i>GitHub Repository</i>. <a href="https:// github.com/jsvine/pdfplumber">https:// github.com/jsvine/pdfplumber</a></div>
  <div class="csl-entry"><i id="zotero|6915743/N3XT428Q"></i>Sinnig, J., &#38; Zetzsche, D. A. (2023). <i>The Impact of the Draft “Unshell Directive” on Luxembourg-based Collective Investment Undertakings</i> (SSRN Scholarly Paper No. 4596578). <a href="https://doi.org/10.2139/ssrn.4596578">https://doi.org/10.2139/ssrn.4596578</a></div>
  <div class="csl-entry"><i id="zotero|6915743/DQ7RGENX"></i>Thomas, B. (2014). How the West Was Won. <i>Lëtzebuerger Land</i>. <a href="https://www.land.lu/page/article/416/7416/FRE/index.html">https://www.land.lu/page/article/416/7416/FRE/index.html</a></div>
  <div class="csl-entry"><i id="zotero|6915743/EB38VNIX"></i>Van Fossen, A. B. (2012). <i>Tax Havens and Sovereignty in the Pacific Islands</i>. Univ. of Queensland Press.</div>
  <div class="csl-entry"><i id="zotero|6915743/ZANTZ8SS"></i>Volkmann, H.-E. (2010). <i>Luxemburg im Zeichen des Hakenkreuzes : eine politische Wirtschaftsgeschichte 1933 bis 1944</i> (benoit-bxl). Schöningh.</div>
  <div class="csl-entry"><i id="zotero|6915743/MJWQASUP"></i>Walther, O., Schulz, C., &#38; Dörry, S. (2011). Specialised international financial centres and their crisis resilience: The case of Luxembourg. <i>Geographische Zeitschrift</i>, <i>99</i>(2/3), 123–142. <a href="http://www.jstor.org/stable/23226598">http://www.jstor.org/stable/23226598</a></div>
  <div class="csl-entry"><i id="zotero|6915743/DHFSHPT9"></i>Watteyne, S. (2023). <i>Lever l’impôt en Belgique. Une histoire des combats politiques (1830-1962)</i>. CRISP.</div>
  <div class="csl-entry"><i id="zotero|6915743/MTBV75MR"></i>Weber, J. (2013). <i>Familien der Oberschicht in Luxemburg: Elitenbildung &#38; Lebenswelten 1850-1900</i>.</div>
  <div class="csl-entry"><i id="zotero|6915743/P5W589ED"></i>Weitzman, H. (2022). <i>What’s the Matter with Delaware?: How the First State Has Favored the Rich, Powerful, and Criminal—and How It Costs Us All</i>. Princeton University Press. <a href="https://doi.org/10.1515/9780691185774">https://doi.org/10.1515/9780691185774</a></div>
</div>
<!-- BIBLIOGRAPHY END -->
