# PROJECT_PDF
#This is a simple code for converting any  ".docx"  extention files into ".pdf"  extention files
import os
from docx2pdf import convert

def convert_docx_to_pdf(input_folder, output_folder):
    # Ensure output folder exists, create if not
    if not os.path.exists(output_folder):
        os.makedirs(output_folder)

    # List all files in the input folder
    files = os.listdir(input_folder)

    # Find all .docx files
    docx_files = [file for file in files if file.endswith('.docx')]

    if not docx_files:
        print("No .docx files found in the input folder.")
        return
    
    for docx_file in docx_files:
        input_file = os.path.join(input_folder, docx_file)
        output_file = os.path.join(output_folder, os.path.splitext(docx_file)[0] + ".pdf")

        convert(input_file, output_file)
        print(f"Conversion successful: {os.path.basename(input_file)} -> {os.path.basename(output_file)}")

if __name__ == "__main__":
    input_folder = "C:/Users/MOKA GANESH/Desktop/test/input_folder"  # Replace with the path to your input folder
    output_folder = "C:/Users/MOKA GANESH/Desktop/test/output_folder"  # Replace with the path to your output folder

    convert_docx_to_pdf(input_folder, output_folder)
    print("All conversions completed.")
