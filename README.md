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

Berikut adalah cara untuk membuat IBM Cloud Services yang telah disebutkan
1. Jika tidak memiliki akun IBM Cloud, daftarkan akun gratis [disini](https://cloud.ibm.com/registration).
2. Pilih dan buat Watson Assistant dari catalog.
3. Pilih dan buat Watson Discovery dari catalog dan pilih "Plus" plan default.
NOTE: Penggunaan Plus plan dari IBM Watson Discovery dengan penggunaan percobaan gratis 30 hari diawal; dapat ubah ke mode berbayar setelah masa percobaan.
Jika tidak dibutuhkan lagi, Service dapat dihapus.

## **3. Configure Watson Discovery**
Lakukan konfigurasi Watson Discovery dengan memilih Watson Discovery dari Resource List
From the IBM Cloud dashboard, click on your new Discovery service in the resource list.

![image](https://github.com/GlacialIce/GlacialIce.github.io/assets/71811961/b85039a3-5249-49d5-8164-a3609efddc1e)

From the Manage tab panel of your Discovery service, click the Launch Watson Discovery button.

**Create a project and collection**
The landing page for Watson Discovery is a panel showing your current projects.

Create a new project by clicking the New Project tile.

NOTE: The Watson Discovery service queries are defaulted to be performed on all collections within a project. For this reason, it is advised that you create a new project to contain the collection we will be creating for this code pattern.

![image](https://github.com/GlacialIce/GlacialIce.github.io/assets/71811961/e1c96b48-3a2f-456d-9921-decc5333cef6)

Give the project a unique name and select the Document Retrieval option, then click Next.

![image](https://github.com/GlacialIce/GlacialIce.github.io/assets/71811961/e23fe7ff-5507-42c6-90fd-4a49a336d43c)

For data source, click on the Upload data tile and click Next.

![image](https://github.com/GlacialIce/GlacialIce.github.io/assets/71811961/624805ea-54a3-45bf-91a6-329a9f44e015)

Enter a unique name for your collection and click Finish.

**Import the document**
On the Configure Collection panel, click the Drag and drop files here or upload button to select and upload the ecobee3_UserGuide.pdf file located in the data directory of your local repo.

![image](https://github.com/GlacialIce/GlacialIce.github.io/assets/71811961/c0177310-4ba0-44f4-9b59-f9185171b03c)

NOTE: The Ecobee is a popular residential thermostat that has a wifi interface and multiple configuration options.

Once the file is loaded, click the Finish button.

Note that after the file is loaded it may take some time for Watson Discovery to process the file and make it available for use. You should see a notification once the file is ready.

**Access the collection**
To access the collection, make sure you are in the correct project, then click the Manage Collections tab in the left-side of the panel.

![image](https://github.com/GlacialIce/GlacialIce.github.io/assets/71811961/4fbd3b4d-2a0f-409a-9364-8d3b5ea76634)

Click the collection tile to access it.

![image](https://github.com/GlacialIce/GlacialIce.github.io/assets/71811961/00d2fb69-1724-470a-aa64-d7e4b53c28eb)

Before applying Smart Document Understanding (SDU) to our document, lets do some simple queries on the data so that we can compare it to results found after applying SDU. Click the Try it out panel to bring up the query panel.

![image](https://github.com/GlacialIce/GlacialIce.github.io/assets/71811961/0be15bd9-3d1d-4816-9f6e-8148b7bf14aa)

Enter queries related to the operation of the thermostat and view the results. As you will see, the results are not very useful, and in some cases, not even related to the question.

**Annotate with SDU**
Now let's apply SDU to our document to see if we can generate some better query responses.

![image](https://github.com/GlacialIce/GlacialIce.github.io/assets/71811961/40f83a68-a96c-4786-a6ad-c74e09e06915)

From the Define structure drop-down menu, click on New fields.

![image](https://github.com/GlacialIce/GlacialIce.github.io/assets/71811961/a9d5a75b-f576-477d-8d5b-061a24cfb895)

From the Identify fields tab panel, click on User-trained models, the click Submit from the confirmation dialog.

Click the Apply changes and reprocess button in the top right corner. This will SDU process.

Here is the layout of the SDU annotation panel:

![image](https://github.com/GlacialIce/GlacialIce.github.io/assets/71811961/463b9479-7b49-4dba-92d1-45bb4afff310)

The goal is to annotate all of the pages in the document so Discovery can learn what text is important, and what text can be ignored.

[1] is the list of pages in the manual. As each is processed, a green check mark will appear on the page.
[2] is the current page being annotated.
[3] is a graphic display of the same page, but allows you to select regions that you can label.
[4] is the list of labels you can assign to the graphic page.
Click [5] to submit the page to Discovery.
Click [6] when you have completed the annotation process.
To add/change a label, select the new label, then click on the text areas in the graphic page to apply it.

As you go though the annotations one page at a time, Discovery is learning and should start automatically updating the upcoming pages. Once you get to a page that is already correctly annotated, you can stop, or simply click Submit [5] to acknowledge it is correct. The more pages you annotate, the better the model will be trained.

For this specific owner's manual, at a minimum, it is suggested to mark the following:

The main title page as title
The table of contents (shown in the first few pages) as table_of_contents
All headers and sub-headers (typed in light green text) as a subtitle
All page numbers as footers
All circuitry diagram pages (located near the end of the document) as a footer
All licensing information (located in the last few pages) as a footer
All other text should be marked as text.
Click the Apply changes and reprocess button [6] to load your changes. Wait for Discovery to notify you that the reprocessing is complete.

Next, click on the Manage fields [1] tab.

![image](https://github.com/GlacialIce/GlacialIce.github.io/assets/71811961/e84b607c-51b1-42ea-bec7-197ba84d45c1)

[2] Here is where you tell Discovery which fields to ignore. Using the on/off buttons, turn off all labels except subtitles and text.
[3] is telling Discovery to split the document apart, based on subtitle.
Click [4] to submit your changes.
Return to the Activity tab. After the changes are processed (may take some time), your collection will look very different:

![image](https://github.com/GlacialIce/GlacialIce.github.io/assets/71811961/d2275910-1463-41ca-8664-6f7a92dbdbe4)

Return to the query panel (click Try it out) and see how much better the results are.

![image](https://github.com/GlacialIce/GlacialIce.github.io/assets/71811961/bc50a6e6-7840-4c7b-ae9f-24bf1cf89992)

**4. Configure Watson Assistant**
The instructions for configuring Watson Assistant for IBM Cloud.
Find the Assistant service in your IBM Cloud Dashboard.

Click on the service and then click on Launch tool.

**Create assistant**
From the main Assistant panel, you will see 2 tab options - Assistants and Skills. An Assistant is the container for a set of Skills.

Go to the Assistant tab and click Create assistant.

![image](https://github.com/GlacialIce/GlacialIce.github.io/assets/71811961/dd536806-c0e5-43b8-b173-c282c51f4c90)

Give your assistant a unique name then click Create assistant.

Create Assistant dialog skill
You will then be taken to a panel that shows the Skills assigned to your Assistant. You can also revisit this panel by selected the desired Assistant listed in the Assistants tab panl.

![image](https://github.com/GlacialIce/GlacialIce.github.io/assets/71811961/c5f91dae-53f1-4124-99f6-0a05923cd458)

Click on Add dialog skill.

From the Add Dialog Skill panel, select the Use sample skill tab.

Select the Customer Care Sample Skill as your template.

The newly created dialog skill should now be shown in your Assistant panel:

![image](https://github.com/GlacialIce/GlacialIce.github.io/assets/71811961/29bce45a-8a63-4e01-8df7-2506304ebfe7)

Click on your newly created dialog skill to edit it.

**Add new intent**
The default customer care dialog does not have a way to deal with any questions involving outside resources, so we will need to add this.

Create a new intent that can detect when the user is asking about operating the Ecobee thermostat.

From the Customer Care Sample Skill panel, select the Intents tab.

Click the Create intent button.

Name the intent #Product_Information, and at a minimum, enter the following example questions to be associated with it.

![image](https://github.com/GlacialIce/GlacialIce.github.io/assets/71811961/e1375063-4ff5-4a73-80f1-35c60404a2a5)

**Create new dialog node**
Now we need to add a node to handle our intent. Click on the back arrow in the top left corner of the panel to return to the main panel. Click on the Dialog tab to bring up the nodes defined for the dialog.

Select the What can I do node, then click on the drop down menu and select the Add node below option.

![image](https://github.com/GlacialIce/GlacialIce.github.io/assets/71811961/be5febe6-9e83-444e-8367-93474dd25f89)

Name the node "Ask about product" [1] and assign it our new intent [2].

![image](https://github.com/GlacialIce/GlacialIce.github.io/assets/71811961/dd21af7e-8c98-4e14-806b-00763ce45f1b)

In the Assistant responds dropdown, select the option Search skill.

This means that if Watson Assistant recognizes a user input such as "how do I set the time?", it will direct the conversation to this node, which will integrate with the search skill.

**Create Assistant search skill**
Return to the Skills panel by clicking the Skills icon in the left menu pane.

From your Assistant skills panel, click on Create skill.

For Skill Type, select Search skill and click Next.

Note: If you have provisioned Watson Assistant on IBM Cloud, the search skill is only offered on a paid plan, but a 30-day trial version is available if you click on the Plus button.

Give your search skill a unique name, then click Continue.

From the search skill panel, select the Discovery service instance and collection you created previously.

![image](https://github.com/GlacialIce/GlacialIce.github.io/assets/71811961/0521ceb1-1b6b-474e-ba74-90583fa0e74f)

Click Configure to continue.

From the Configure Search Response panel, select text as the field to use for the Body of the response.

![image](https://github.com/GlacialIce/GlacialIce.github.io/assets/71811961/fa42a177-a980-4d35-bc42-41b0311b5006)

You can also customize the return Message to be more appropriate for your use case.

Click Create to complete the configuration.

Now when the dialog skill node invokes the search skill, the search skill will query the Discovery collection and display the text result to the user.

**Test in Assistant Tooling**
NOTE: The following feature is currently only available for Watson Assistant provisioned on IBM Cloud.

You should now see both skills have been added to your assistant.

![image](https://github.com/GlacialIce/GlacialIce.github.io/assets/71811961/9fdba157-5eeb-4471-99af-2342b16e5499)

Normally, you can test the dialog skill be selecting the Try it button located at the top right side of the dialog skill panel, but when integrated with a search skill, a different method of testing must be used.

From your assistant panel, select Preview link.

![image](https://github.com/GlacialIce/GlacialIce.github.io/assets/71811961/106ebaf8-57ca-4933-9ba8-8cbc12654f01)

From the list of available integration types, select Preview link.

If you click on the generated URL link, you will be able to interact with your dialog skill. Note that the input "how do I turn on the heater?" has triggered our Ask about product dialog node and invoked our search skill.

![image](https://github.com/GlacialIce/GlacialIce.github.io/assets/71811961/50b0970f-27ed-463a-8196-59e37d736f5a)

## **5. Integration from Watson Discovery to Watson Assistant**

Langkah-langkah melakukan integrasi Watson Discovery ke Watson Assistant :
1. Pergi ke tab Integration di Watson Assistant
![Image](https://github.com/GlacialIce/GlacialIce.github.io/assets/71811961/ab49d9dc-1dfe-4a43-a854-7bec46308ebe)

2. Pilih bagian "search", dapat pilih "draft" atau "live". Namun, untuk penggunaan di production, pilih "live"
![Image](https://github.com/GlacialIce/GlacialIce.github.io/assets/71811961/4ff1990e-f401-4aa5-bef2-91e8b3754b13)

3. Pastikan tampilan seperti di gambar, dengan posisi sistem mendeteksi Watson Discovery yang telah kita buat
![Image](https://github.com/GlacialIce/GlacialIce.github.io/assets/71811961/d652fca5-199d-4912-ac15-3f076f74d9f9)
![Image](https://github.com/GlacialIce/GlacialIce.github.io/assets/71811961/d13086f7-fe3a-449e-94bc-89a1be4e3434)

4. Tekan "save" untuk menyimpan konfigurasi yan telah dibuat
![Image](https://github.com/GlacialIce/GlacialIce.github.io/assets/71811961/19d8295b-831d-4f23-bede-d4798282bae9)

## **6. Run the Application**
Aplikasi ini dapat dijalankan melalui link berikut :
https://glacialice.github.io/
