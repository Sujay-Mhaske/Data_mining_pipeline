# Data_mining_pipeline

#############################################################
# 1.txt contains pages to infinity
# 2.txt will contain all https from respective pages in 1.txt

import requests
from bs4 import BeautifulSoup
import sys
file = open("1.txt", 'r')
Lines = file.readlines()
for line in Lines:
    url = line.strip()
    reqs = requests.get(url)
    soup = BeautifulSoup(reqs.text, 'html.parser')

    urls = []
    for link in soup.find_all('a'):
        sys.stdout = open("2.txt", "a", encoding="utf-8")
        print(link.get('href'))

#############################################################
# 3.txt will contain all lines/links from 2.txt ending with html # # .html

file1 = open('2.txt','r')

file2 = open('3.txt','w')

for line in file1.readlines():
        if  line.strip().endswith('html'):
            print(line)
            file2.write(line)

file2.close()
file1.close()

#############################################################
# 4.txt will be without duplicates as in 3.txt
# following program will remove duplicates

import hashlib

output_file_path = "4.txt"
input_file_path = "3.txt"

completed_lines_hash = set()

output_file = open(output_file_path, "w")

for line in open(input_file_path, "r"):

  hashValue = hashlib.md5(line.rstrip().encode('utf-8')).hexdigest()

  if hashValue not in completed_lines_hash:
    output_file.write(line)
    completed_lines_hash.add(hashValue)

output_file.close()

#############################################################
# following program will get link per line , get source code 
# and print line containing .mp4 in final.txt

import wget
url = 'http://www.futurecrew.com/skaven/song_files/mp3/razorback.mp3'
filename = wget.download(url)
filename

to download

#############################################################
import requests
import sys
file = open("4.txt", 'r', encoding='utf-8')
Lines = file.readlines()
for line in Lines:
    url = line.strip()
    reqs = requests.get(url)
    txt = reqs.text
    sys.stdout = open("htmlsource.txt", "w", encoding="utf-8")
    print(txt)
    searchfile = open("htmlsource.txt", "r", encoding='utf-8')
    for line in searchfile:
        if '.mp4' in line:
            sys.stdout = open("ll.txt", "a", encoding="utf-8")
            print(line)

#####################################################################

bad_words = ['bad', 'naughty']

with open('oldfile.txt') as oldfile, open('newfile.txt', 'w') as newfile:
    for line in oldfile:
        if not any(bad_word in line for bad_word in bad_words):
            newfile.write(line)

import sys
pages = 617
i = 0
for i in range(1, pages):
        sys.stdout = open("1.txt", "a", encoding="utf-8")
        print("", end="")
        print(i, end="")
        print("/")
        pages = pages + 1

#########################################################


print(re.findall(r'([^\s]+)', line))



import requests
import sys
import time
import glob
file = open("4.txt", 'r', encoding='utf-8')
Lines = file.readlines()
for line in Lines:
    url = line.strip()
    line1 = url
    reqs = requests.get(url)
    txt = reqs.text
    with open("htmlsource.txt", "w", encoding="utf-8") as htmlsource:
        htmlsource.write(txt)
        with open("htmlsource.txt", "r", encoding='utf-8') as searchfile:
            for line in searchfile:
                if '.mp4' in line:
                    with open("ll.txt", "a", encoding="utf-8") as file1:
                        file1.write(line1)
                        file1.write(line)

##############################################################################################

import glob
import sys
import os
path = "C:\\Users\\Sujay\\PycharmProjects\\tp\\New folder\\parts\\*.txt"
for files in glob.glob(path):
    filename = os.path.basename(files)
    filename1 = os.path.splitext(filename)[0]

    with open(files) as infile, open(filename1+'aa.txt', 'w') as outfile:
        for line in infile:
            if not line.strip(): continue
            outfile.write(line)
##############################################################################################

with open('2.txt') as f:                # 1 minus 2 equals 3
    bad_words = f.read().splitlines()
    # print(lines)
    with open('1.txt') as oldfile, open('3.txt', 'w') as newfile:
        for line in oldfile:
            if not any(bad_word in line for bad_word in bad_words):
                newfile.write(line)
