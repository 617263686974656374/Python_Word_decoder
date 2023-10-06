"""
Program Name: Word Decoder
Author: Jaroslav
Date: 25.03.2023
Description:
   This program is used to decode words. If you enter a word, for example: "oordpots",
    the program will find a suitable decoded word according to the predefined dictionary,
    in this case it will find the word: "doorpost"
"""

import collections

# Load words from the provided filename
def load_words(filename):
    with open(filename, 'r') as file:
        # Read all words and split by lines
        words = file.read().splitlines()
    return words

# Check if two words have a minimum number of common letters
def has_common_letters(word1, word2, min_common=3):
    # Count the number of common letters between the two words
    common_count = sum([1 for letter in set(word1) if letter in word2])
    # Check if common letters count meets the minimum requirement
    return common_count >= min_common

# Find a word in the dictionary that matches the given word
def find_matching_word(word, dictionary):
    # Find potential candidates that have common letters with the word
    candidates = [candidate for candidate in dictionary if has_common_letters(word, candidate)]

    # Sort the letters of the word
    sorted_word = "".join(sorted(word))
    for candidate in candidates:
        # Check if candidate matches the sorted word
        if sorted_word == "".join(sorted(candidate)):
            return candidate
    # If no match found, return None
    return None

# Decode a string of encoded words based on the dictionary
def decode_words(encoded_words_str, dictionary):
    # Split the encoded string into individual words
    encoded_words = encoded_words_str.split(';')
    decoded_words = []

    for word in encoded_words:
        # Find the decoded word for each encoded word
        decoded_word = find_matching_word(word, dictionary)
        if decoded_word:
            decoded_words.append(decoded_word)
        else:
            # If word is not found in dictionary, append "Nenájdené"
            decoded_words.append("Not found")

    # Join the decoded words into a single string
    return ';'.join(decoded_words)

# Main function to run the program
def main():
    # Load words from the dictionary file
    words = load_words("slovnik.txt")
    # Ask the user for input
    encoded_words_str = input("Enter encoded words separated by semicolons: ")
    # Decode the input words
    decoded_words_str = decode_words(encoded_words_str, words)

    # Display the decoded words
    print(f"Decoded words: {decoded_words_str}")


if __name__ == "__main__":
    main()
