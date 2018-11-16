---
title: 支援的網站範本 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- we site projects, templates
ms.assetid: 37173c97-486b-4b3c-8ed3-cf5890c4de23
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: eebacb3006826a90320cbc61edf7d56467e688ce
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51760225"
---
# <a name="web-site-support-templates"></a>網站支援範本
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 網站專案和項目範本會提供可重複使用且可自訂的網站專案和項目虛設常式，並不需要從頭開始建立新的網站專案和項目，來加速開發程序。 如需詳細資訊[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]範本，請參閱[建立專案和項目範本](../../ide/creating-project-and-item-templates.md)。  
  
## <a name="project-template-folder"></a>專案範本資料夾  
 Web 專案範本的範本通常會安裝在 [*Visual Studio 安裝路徑*] \Common7\IDE\ProjectTemplates\Web\\，每個 web 程式設計語言所命名的子資料夾中。  
  
## <a name="project-file"></a>專案檔  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]整合式的開發環境 (IDE)，以便將範本對應至正確的專案類型需要專案副檔名。 因為 Web 專案沒有專案檔，dummy 專案檔案的副檔名.webproj 會註冊為支援此功能。  
  
 語言名稱字串 （選擇性） 加入範本中，讓 Web 專案系統中設定預設語言**加入新項目**以範本為基礎的項目 對話方塊。 字串必須是檔案的第一行，而且必須符合註冊下 AddItemLanguageName Intellisense 引擎註冊中的名稱和專案 Subtype(VsTemplate) 下註冊的名稱。 如需詳細資訊，請參閱 <<c0> [ 網站支援屬性](../../extensibility/internals/web-site-support-attributes.md)。  
  
 如果字串不存在，Web 專案系統會嘗試判斷 Web 專案範本加入的專案範本的頁面的語言屬性和檔案延伸模組為基礎的預設語言。  
  
## <a name="project-templates"></a>專案範本  
 網站專案範本用來建立新的網站以回應**New Web Site**命令**檔案**功能表。 目前支援三個網站專案類型：  
  
-   空白網站專案  
  
-   網站專案  
  
-   Web 服務專案  
  
### <a name="empty-web-site-projects"></a>空白網站專案  
 這些檔案建立新的空網站，以回應**空網站**命令，之後可供使用指向**新的網站**上**檔案**功能表：  
  
-   EmptyWeb.vstemplate  
  
     引導建立新的空白網站範本檔案。  
  
-   EmptyWeb.webproj  
  
     這個檔案是專案範本系統的成品。 它可滿足 EmptyWeb.vstemplate 檔案中的專案檔案參考。  
  
### <a name="web-site-projects"></a>網站專案  
 這些檔案建立新的網站，以回應**ASP.NET Web Site**命令，之後可供使用指向**新的網站**上**檔案**功能表：  
  
-   Default.aspx  
  
     新的網站預設首頁。 Language 屬性會指定程式碼後置的語言和 CodeFile 屬性指定包含此頁面相關聯的程式碼後置程式碼的相依檔案。  
  
-   Default.aspx。*延伸模組*  
  
     包含預設的首頁的程式碼後置程式碼的相依檔案。 程式碼後置語言會決定*延伸模組*此檔案。  
  
-   web.config  
  
     根 web.site 組態檔中。  
  
-   WebApplication.vstemplate  
  
     範本檔案，會決定內容的網站解決方案，並強制建立的 [App_Data] 資料夾。  
  
-   WebApplication.webproj  
  
     這個檔案是專案範本系統的成品。 它可滿足 WebApplication.vstemplate 檔案中的專案檔案參考。  
  
### <a name="web-service-projects"></a>Web 服務專案  
 這些檔案建立新的網站，以回應**ASP.NET Web 服務**命令，這是在之後，指向**新的網站**上**檔案**功能表：  
  
-   Service.asmx  
  
     HTML 網頁進行新的 Web 服務。 Language 屬性會指定程式碼後置的語言和程式碼後置屬性指定包含此服務相關聯的程式碼後置程式碼的相依檔案。  
  
-   服務。 *延伸模組*  
  
     實作服務類別的相依檔案。 程式碼後置語言會決定*延伸模組*此檔案。  
  
-   web.config  
  
-   根 web.site 組態檔中。  
  
-   WebService.vstemplate  
  
     範本檔案，會決定內容的網站解決方案，並強制 App_Data 和 App_Code 資料夾的建立。 此服務。*延伸模組*檔案複製到 App_Code 資料夾。  
  
-   WebService.webproj  
  
     這個檔案是專案範本系統的成品。 它可滿足 WebService.vstemplate 檔案中的專案檔案參考。  
  
## <a name="project-item-template-folder"></a>專案項目範本資料夾  
 Web 專案項目範本的範本通常會安裝在 [*Visual Studio 安裝路徑*] \Common7\IDE\ItemTemplates\Web\\，其 web 程式設計語言所命名的子資料夾中的每個。  
  
## <a name="project-item-templates"></a>專案項目範本  
 網站專案項目範本用來將新的網頁新增至網站，以回應**加入現有項目**命令。 目前支援這種網頁：  
  
-   新的類別  
  
-   新的 HTML 網頁  
  
-   新的 Web Form  
  
-   新的主版頁面  
  
### <a name="new-class"></a>新的類別  
 此範本會建立新的原始程式檔定義空的類別，以回應**加入新類別**命令。  
  
-   類別。 *延伸模組*  
  
     實作空的類別原始程式檔。 程式碼後置語言會決定*延伸模組*此檔案。  
  
-   Class.vstemplate  
  
     範本檔案，會建立原始程式檔，並判斷其內容。  
  
### <a name="new-html-page"></a>新的 HTML 網頁  
 此範本會建立新的 Web 網頁以回應**加入新的 HTML 網頁**命令。  
  
-   HTMLPage.htm  
  
     起始網頁的內容。 這個 Web 網頁通常會有任何相關聯的程式碼後置相依檔案。 若要建立智慧型的頁面與相關聯的程式碼後置檔案，請改為使用 Web 表單範本。  
  
-   HTMLPage.vstemplate  
  
     範本檔案，建立網頁，並判斷其內容。  
  
### <a name="new-webform"></a>新的 WebForm  
 此範本會建立新的智慧型網頁以回應**加入新的 Web Form**命令。  
  
 若要建立相依的程式碼後置原始程式檔，請選取**程式碼置於個別檔案**。 否則，會建立具有空的指令碼區塊，但沒有單一的 Web 網頁\<%page%> 指示詞來連結相依檔案。  
  
 若要建立所選取的主版頁面的內容頁面，選取**選取的主版頁面**。  
  
-   WebForm.aspx  
  
     起始網頁的內容。 這個 Web 網頁有沒有相關聯的程式碼後置相依檔案。  
  
-   WebForm_cb.aspx  
  
     起始網頁的內容。 這個 Web 網頁有相關聯的程式碼後置相依檔案。  
  
-   程式碼後置。 *延伸模組*  
  
     實作 webform 類別的相依檔案。 程式碼後置語言會決定*延伸模組*此檔案。  
  
-   ContentPage.aspx  
  
     起始網頁做為內容頁面的內容。 這個 Web 網頁有沒有相關聯的程式碼後置相依檔案。  
  
-   ContentPage_cb.aspx  
  
     起始網頁做為內容頁面的內容。 這個 Web 網頁有相關聯的程式碼後置相依檔案。  
  
-   WebForm.vstemplate  
  
     範本檔案會決定新的 web 網頁和其相依的檔案的內容，如果有的話。  
  
### <a name="new-master-page"></a>新的主版頁面  
 此範本建立新的主版頁面，以回應**加入新的主版頁面**命令。  
  
 若要建立相依的程式碼後置原始程式檔，請選取**程式碼置於個別檔案**。 否則，會建立具有空的指令碼區塊，但沒有單一的 Web 網頁\<%page%> 指示詞來連結相依檔案。  
  
-   MasterPage.master  
  
     主版頁面的起始內容。 此主版頁面都有沒有相關聯的程式碼後置的相依檔案。  
  
-   MasterPage_cb.master  
  
     主版頁面的起始內容。 此主版頁面都有一個相關聯的程式碼後置的相依檔案。  
  
-   程式碼後置。*延伸模組*  
  
     實作的主版頁面類別的相依檔案。 程式碼後置語言會決定*延伸模組*此檔案。  
  
-   MasterPage.vstemplate  
  
     範本檔案會決定新的主版頁面和其相依的檔案的內容，如果有的話。  
  
## <a name="see-also"></a>另請參閱  
 [網站支援](../../extensibility/internals/web-site-support.md)

