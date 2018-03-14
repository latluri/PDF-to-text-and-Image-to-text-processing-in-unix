# PDF-to-text-and-Image-to-text-processing-in-linux/Unix
If you are in linux/Unix environment and would like to extract the text from any of the PDF,Image or Scanned printout, you could avail these code

# Scenario 1: Computer generated PDF to Text
A normal PDF generated from a word/excel files have author names, codec information, creation information and can be converted into a plain text format  
Use the following codes in Linux/Unix cluster
# option 1 Ghost scripts
gs -sDEVICE=txtwrite -o output.txt input.pdf 

Manpage- https://www.ghostscript.com/doc/9.19/VectorDevices.htm

# option 2 
pdftotext -layout input.pdf output.txt

Options include first page, last page, resolution, layout etc
find the documation in this link 
https://linux.die.net/man/1/pdftotext

The file output contains the required text
You can use the awk, grep, perl commands to extract the data from this unstructured text file




# Scenario 2: Scanner generated PDF to Text
Now consider having a printout of a file containing text that you would like to extract.
You could use scanners that convert this hard copy into a soft copy, however you would loose vital information on decoding it. 
Normal pdf to word converters would not be useful here 

One way of dealing with this is 
Convert PDF to Image and then Image to text
This is because the scanners capture the image of the printout and converts this "image" to PDF to meet the customers' demand for a pdf file.

# Converting to Image

option 1 
pdfimages input.pdf outputImage

Option2
pdftocairo -W 4000 -H 1800 -q -jpeg input.pdf outputImage

# Extract text from Image
Tesseract is an optical character recognition engine for various operating systems. It is free software, released under the Apache License, Version 2.0, and development has been sponsored by Google since 2006.


tesseract outputImage.pbm outputText

The file output contains the required text
You can use the awk, grep, perl commands to extract the data from this unstructured text file


