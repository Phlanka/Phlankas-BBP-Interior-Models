# Phlanka BBP Interior Models Collection Catalogue

This repository contains the Phlanka BBP Interior Models Collection Catalogue, which can be added to your Blender setup.

## Installation Instructions

You can install these models into your collection catalogue:

1. Open Blender and navigate to the **Scripting** tab.
2. Click the **+ New** button to create a new text document.
3. Copy and paste the following script into the text editor:

```python
import os
import zipfile
import urllib.request

def download_file_from_github(url, destination):
    with urllib.request.urlopen(url) as response, open(destination, 'wb') as out_file:
        data = response.read()
        out_file.write(data)

def extract_assets(zip_path, target_directory):
    if not os.path.exists(target_directory):
        os.makedirs(target_directory)
    with zipfile.ZipFile(zip_path, 'r') as zip_ref:
        zip_ref.extractall(target_directory)

url = 'https://github.com/Phlanka/Phlankas-BBP-Interior-Models/raw/main/Phlankas%20BBP%20Collection%20Models.zip'
zip_path = os.path.join(os.path.expanduser("~"), "assets.zip")


appdata_path = os.getenv('APPDATA')
target_directory = os.path.join(appdata_path, "Blender Foundation", "Blender", "4.3", "scripts", "addons")

download_file_from_github(url, zip_path)
extract_assets(zip_path, target_directory)
os.remove(zip_path)
```

4. Click the **Run Script** button to execute the script.

This script will automatically download and extract the assets into your Blender addons directory.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
