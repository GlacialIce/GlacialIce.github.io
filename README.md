# Sistem Chatbot Berbasis Aplikasi Web Untuk Informasi Manajemen Pengolahan Sampah Padat

Sistem Chatbot Berbasis Aplikasi Web Untuk Informasi Manajemen Pengolahan Sampah Padat adalah aplikasi chatbot yang dibuat dengan tujuan untuk 
menjadi sarana edukasi terkait manajemen sampah padat, tata cara pengolahannya, dan tata cara untuk memindahkannya dari satu tempat ke tempat lainnya. 

## **Important Notes**
What is SDU ? 
SDU trains Watson Discovery to extract custom fields in your documents. Customizing how your documents are indexed into Discovery will improve the answers returned from queries.

With SDU, you annotate fields within your documents to train custom conversion models. As you annotate, Watson is learning and will start predicting annotations. SDU models can also be exported and used on other collections.

Current document type support for SDU is based on your plan:

Lite plans: PDF, Word, PowerPoint, Excel, JSON, HTML
Advanced plans: PDF, Word, PowerPoint, Excel, PNG, TIFF, JPG, JSON, HTML

File yang digunakan untuk chatbot ini : 
https://ec.europa.eu/echo/files/evaluation/watsan2005/annex_files/WEDC/es/ES07CD.pdf

- Note : Aplikasi ini dibuat sebagai bagian dari laporan akhir MBKM Studi Independen PT Kinema Systrans Multimedia (Infinite Learning)

## **Flow**
![image](https://github.com/GlacialIce/GlacialIce.github.io/assets/71811961/276478a2-d7bd-4d86-8f3d-68c1a2f89b66)

Penjelasan Flow :
1. Dokumen tersebut dianotasi menggunakan Watson Discovery SDU
2. Pengguna berinteraksi dengan server backend melalui UI aplikasi. UI aplikasi frontend adalah chatbot yang melibatkan pengguna dalam percakapan.
3. Dialog antara pengguna dan server backend dikoordinasikan menggunakan keterampilan dialog Asisten Watson.
4. Jika pengguna mengajukan pertanyaan operasi produk, permintaan pencarian dikeluarkan ke layanan Watson Discovery melalui keterampilan pencarian Asisten Watson.

## **Langkah - langkah :**
1. Clone the repo
2. Create Watson services
3. Configure Watson Discovery
4. Configure Watson Assistant
5. Integration from Watson Discovery to Watson Assistant
6. Run the Appliaction

## **1. Clone the Repo**
git clone https://github.com/IBM/watson-assistant-with-search-skill

## **2. Create Watson Services**
Buatlah IBM Cloud Services sebagai berikut :
- Watson Assistant
- Watson Discovery


- Watson DiscoveryWatk
