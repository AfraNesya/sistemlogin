# tugas_sistem_login 
<br>
Sistem Login dengan Enkripsi Vigenere Chipper <br>
-------------------------------------------------------- <br>
Nama              : Afra Nesya Apriyanthi <br>
NIM               : 312110614 <br>
Mata Kuliah       : Kriptografi <br>
Dosen Pengampu    : Ahmad Turmudi Zy, S.Kom., M.Kom <br>
<br>
<br>

```py
def encrypt(text, key):
    encrypted_text = ""
    key_length = len(key)
    for i in range(len(text)):
        char = text[i]
        if char.isalpha():
            key_char = key[i % key_length]
            key_shift = ord(key_char.lower()) - ord('a')
            if char.islower():
                encrypted_char = chr(((ord(char) - ord('a') + key_shift) % 26) + ord('a'))
            else:
                encrypted_char = chr(((ord(char) - ord('A') + key_shift) % 26) + ord('A'))
            encrypted_text += encrypted_char
        else:
            encrypted_text += char
    return encrypted_text



def decrypt(text, key):
    decrypted_text = ""
    key_length = len(key)
    for i in range(len(text)):
        char = text[i]
        if char.isalpha():
            key_char = key[i % key_length]
            key_shift = ord(key_char.lower()) - ord('a')
            if char.islower():
                decrypted_char = chr(((ord(char) - ord('a') - key_shift) % 26) + ord('a'))
            else:
                decrypted_char = chr(((ord(char) - ord('A') - key_shift) % 26) + ord('A'))
            decrypted_text += decrypted_char
        else:
            decrypted_text += char
    return decrypted_text

# Contoh penggunaan
def main():
    username = "afra"
    password = "afranesya"
    key = "secretkey"  # Ganti dengan kunci rahasia yang lebih kuat dalam aplikasi yang sebenarnya

    # Enkripsi password sebelum disimpan
    encrypted_password = encrypt(password, key)

    # Simpan username dan password terenkripsi dalam basis data atau penyimpanan yang aman
    database = {"username": username, "password": encrypted_password}

    # Proses login
    input_username = input("Masukkan username: ")
    input_password = input("Masukkan password: ")

    if input_username == database["username"] and decrypt(database["password"], key) == input_password:
        print("Login berhasil!")

        # Tampilkan hasil enkripsi dan dekripsi
        print(f"Password terenkripsi: {encrypted_password}")
        decrypted_password = decrypt(database["password"], key)
        print(f"Password terdekripsi: {decrypted_password}")
    else:
        print("Login gagal!")

if __name__ == "__main__":
    main()
```

#Apabila di running maka, masukan username dan password kemudian hasil nya akan seperti ini <br>
!(Screenshot 2023-10-13 182524.png)
