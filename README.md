# Install required libraries
!pip install deep-translator

# Import the translator
from deep_translator import GoogleTranslator

# Supported languages
LANGUAGES = {
    'Afrikaans': 'af', 'Arabic': 'ar', 'Bengali': 'bn', 'Chinese (Simplified)': 'zh-cn',
    'French': 'fr', 'German': 'de', 'Gujarati': 'gu', 'Hindi': 'hi',
    'Japanese': 'ja', 'Korean': 'ko', 'Punjabi': 'pa', 'Russian': 'ru',
    'Spanish': 'es', 'Tamil': 'ta', 'Telugu': 'te'
}

# 🔹 Input text
text = input("✍ Enter text to translate: ")

# 🔹 Choose source language
print("\nAvailable languages:", ", ".join(LANGUAGES.keys()))
source_lang = input("Select source language (or type 'auto' for auto-detect): ")
target_lang = input("Select target language: ")

# 🔹 Perform translation
try:
    translated_text = GoogleTranslator(
        source="auto" if source_lang.lower() == "auto" else LANGUAGES.get(source_lang, "auto"),
        target=LANGUAGES.get(target_lang, "en")
    ).translate(text)

    print("\n✅ Translation Successful!")
    print("📝 Translated Text:", translated_text)

except Exception as e:
    print(f"\n❌ Translation failed: {e}")
