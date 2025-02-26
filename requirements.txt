import streamlit as st

# Conversion dictionaries
letters = {
    '0': 'A', '1': 'B', '2': 'C', '3': 'D', '4': 'E',
    '5': 'F', '6': 'G', '7': 'H', '8': 'I', '9': 'J'
}

morse_code = {
    '0': '-----', '1': '.----', '2': '..---', '3': '...--', '4': '....-',
    '5': '.....', '6': '-....', '7': '--...', '8': '---..', '9': '----.'
}

nato_alphabet = {
    '0': 'Zero', '1': 'One', '2': 'Two', '3': 'Three', '4': 'Four',
    '5': 'Five', '6': 'Six', '7': 'Seven', '8': 'Eight', '9': 'Nine'
}

def convert_to_lmn(number):
    letter_result = ''.join(letters.get(digit, '') for digit in str(number))
    morse_result = ' '.join(morse_code.get(digit, '') for digit in str(number))
    nato_result = ' '.join(nato_alphabet.get(digit, '') for digit in str(number))
    return letter_result, morse_result, nato_result

def main():
    st.set_page_config(page_title="Digit to LMN Converter", page_icon="🔢", layout="wide")

    st.title("Digit to LMN Converter")
    st.write("Convert digits to Letters, Morse code, and NATO phonetic alphabet")

    # Input for the number
    number = st.text_input("Enter a number:", "")

    if number:
        if number.isdigit():
            letter_result, morse_result, nato_result = convert_to_lmn(number)

            st.subheader("Conversion Results:")
            
            col1, col2, col3 = st.columns(3)
            
            with col1:
                st.markdown("### Letters")
                st.write(letter_result)
            
            with col2:
                st.markdown("### Morse Code")
                st.write(morse_result)
            
            with col3:
                st.markdown("### NATO Phonetic")
                st.write(nato_result)

        else:
            st.error("Please enter a valid number (digits only).")

    # Explanation of the conversion
    st.markdown("---")
    st.subheader("How it works:")
    st.write("""
    - **Letters**: Each digit is converted to a letter (0=A, 1=B, ..., 9=J).
    - **Morse Code**: Each digit is converted to its Morse code representation.
    - **NATO Phonetic**: Each digit is converted to its NATO phonetic alphabet word.
    """)

    # Display conversion tables
    st.markdown("---")
    st.subheader("Conversion Tables")
    
    col1, col2, col3 = st.columns(3)
    
    with col1:
        st.markdown("### Letters")
        for digit, letter in letters.items():
            st.write(f"{digit} = {letter}")
    
    with col2:
        st.markdown("### Morse Code")
        for digit, code in morse_code.items():
            st.write(f"{digit} = {code}")
    
    with col3:
        st.markdown("### NATO Phonetic")
        for digit, word in nato_alphabet.items():
            st.write(f"{digit} = {word}")

if __name__ == "__main__":
    main()

