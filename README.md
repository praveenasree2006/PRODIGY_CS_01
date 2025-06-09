# PRODIGY_CS_01
def caesar_cipher(text, shift, mode):
    result = ""

    for char in text:
        if char.isalpha():
            base = ord('A') if char.isupper() else ord('a')
            if mode == 'encrypt':
                shifted = (ord(char) - base + shift) % 26 + base
            elif mode == 'decrypt':
                shifted = (ord(char) - base - shift) % 26 + base
            result += chr(shifted)
        else:
            # Non-alphabet characters are added without change
            result += char

    return result

def main():
    print(" Caesar Cipher Tool ")

    message = input("Enter your message: ")
    while True:
        try:
            shift = int(input("Enter shift value (e.g. 3): "))
            break
        except ValueError:
            print("Please enter a valid number.")

    while True:
        mode = input("Choose mode - encrypt or decrypt: ").lower()
        if mode in ['encrypt', 'decrypt']:
            break
        else:
            print("Invalid mode. Please type 'encrypt' or 'decrypt'.")

    result = caesar_cipher(message, shift, mode)
    print(f"\nResult ({mode.title()}ed): {result}")

if __name__ == "__main__":
    main()
