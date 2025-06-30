"""
Użyj biblioteki Docling do pobrania treści artykułu podanego jako URL,
następnie zapisz wyniki analizy do osobnego pliku JSON w katalogu 'results/'.

Działaj zgodnie z poniższymi krokami:
1. Pobierz zawartość artykułu korzystając z podanego URL.
2. Użyj biblioteki Docling do przetworzenia treści artykułu.
3. Zapisz przetworzone dane jako plik JSON w katalogu 'results/'.

Przykład:
URL: https://example.com/artykul
Wyjście: results/artykul.json

Zaimplementuj skrypt w Pythonie.
"""

import requests
import json
from docling import Docling
import os
from urllib.parse import urlparse

def save_article_analysis(url):
    response = requests.get(url)
    response.raise_for_status()

    docling = Docling()
    analyzed_data = docling.analyze(response.text)

    parsed_url = urlparse(url)
    file_name = os.path.basename(parsed_url.path.strip('/')) or 'article'
    output_dir = 'results'

    if not os.path.exists(output_dir):
        os.makedirs(output_dir)

    output_path = os.path.join(output_dir, f"{file_name}.json")

    with open(output_path, 'w', encoding='utf-8') as f:
        json.dump(analyzed_data, f, ensure_ascii=False, indent=4)

    print(f"Analysis saved to {output_path}")

# Przykład użycia:
# save_article_analysis('https://example.com/artykul')
