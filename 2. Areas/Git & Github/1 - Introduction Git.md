---
tags:
  - git
  - area
Links: "[[My Areas]]"
---
---
# Git Command (Local) Example
- git init
- git add <file(s)>
- git status
- git commit
- git config
- git branch
- git help

# Git Area Workflow
Pada saat membuat repo dengan git, git akan mengidentifikasi repo tersebut menjadi tiga area. 
- _Working Tree_ adalah folder yang berisi banyak file project yang telah/akan dibuat. Untuk menginisialisasi folder tersebut dan menyimpannya ke dalam _Staging Area_ perlu menuliskan : ___git add <file(s)>___ atau ___git add .___ (untuk menyimpan semua perubahan file ke dalam *Staging Area*)
- *Staging Area* adalah perubahan yang terjadi di dalam folder yang berisi file project (Disimpan di dalam folder .git). Jika file telah diinisialisasi dan masuk ke dalam _Staging Area_, untuk melakukan penyimpanan sebagai commit perlu menuliskan perintah : ___git commit___
- *History* adalah Perubahan yang tersimpan dan ini telah menjadi commit (Disimpan di dalam folder .git)