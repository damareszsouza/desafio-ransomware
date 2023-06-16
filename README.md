# desafio-ransomware
#conteudos de pesquisas iniciai 
----------------------------------
from cryptography.fernet import Fernet

# gerar chave para criptografar o arquivo
key = Fernet.generate_key()

# criptografar o arquivo usando a chave gerada
fernet = Fernet(key)
with open('arquivo.txt', 'rb') as file:
    original = file.read()
encrypted = fernet.encrypt(original)

# descriptografar o arquivo criptografado
fernet = Fernet(key)
decrypted = fernet.decrypt(encrypted)
with open('arquivo.txt', 'wb') as file:
    file.write(decrypted)

# Exemplo 1 

import os
import pyaes

## abrir o arquivo criptografado
file_name = "teste.txt.ransomwaretroll"
file = open(file_name, "rb")
file_data = file.read()
file.close()

## chave para descriptografia
key = b"testeransomwares"
aes = pyaes.AESModeOfOperationCTR(key)
decrypt_data = aes.decrypt(file_data)

## remover o arquivo criptografado
os.remove(file_name)

## criar o arquivo descriptografado
new_file = "teste.txt"
new_file = open(f'{new_file}', "wb")
new_file.write(decrypt_data)
new_file.close()

# exemplo 2 

from simplecrypt import encrypt, decrypt

passkey = 'wow'
str1 = 'I am okay'
cipher = encrypt(passkey, str1)
print(cipher)

# descriptografar o texto cifrado
plain = decrypt(passkey, cipher)
print(plain)
