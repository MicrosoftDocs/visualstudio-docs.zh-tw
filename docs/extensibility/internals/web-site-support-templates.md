---
title: "支援的網站範本 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: we site projects, templates
ms.assetid: 37173c97-486b-4b3c-8ed3-cf5890c4de23
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c4e3d64f77064c04e131853786495c921711f2d0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="web-site-support-templates"></a>支援的網站範本
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]網站專案和項目範本提供可重複使用且可自訂的網站專案和項目 stub，不需要從頭開始建立新的網站專案和項目，以加速開發程序。 如需有關[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]範本，請參閱[建立專案和項目範本](../../ide/creating-project-and-item-templates.md)。  
  
## <a name="project-template-folder"></a>專案範本資料夾  
 Web 專案範本的範本通常會安裝在 [*Visual Studio 安裝路徑*] \Common7\IDE\ProjectTemplates\Web\\，每個 web 程式設計語言所命名的子資料夾中。  
  
## <a name="project-file"></a>專案檔  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]整合式的開發環境 (IDE) 必須有專案副檔名做為範本對應到正確的專案類型的方式。 Web 專案沒有專案檔，因為空專案檔案副檔名.webproj 會註冊為支援此作業。  
  
 語言名稱字串 （選擇性） 加入範本中，讓 Web 專案系統中設定預設語言**加入新項目**範本為基礎的項目 對話方塊。 字串必須是檔案的第一行，而且必須符合下 AddItemLanguageName 註冊在 Intellisense 引擎註冊的名稱和專案 Subtype(VsTemplate) 下註冊的名稱。 如需詳細資訊，請參閱[網站支援屬性](../../extensibility/internals/web-site-support-attributes.md)。  
  
 如果字串不存在，Web 專案系統會嘗試判斷頁面的 Web 專案範本加入的專案範本的語言屬性和檔案延伸模組為基礎的預設語言。  
  
## <a name="project-templates"></a>專案範本  
 網站專案範本可用來建置新網站，以回應**新網站**命令**檔案**功能表。 目前支援三個網站專案類型：  
  
-   空白網站專案  
  
-   網站專案  
  
-   Web 服務專案  
  
### <a name="empty-web-site-projects"></a>空白網站專案  
 這些檔案建立新的空白網站以回應**空白網站**命令之後指向, 可供使用**新網站**上**檔案**功能表：  
  
-   EmptyWeb.vstemplate  
  
     輔助線建立新的空白網站範本檔案。  
  
-   EmptyWeb.webproj  
  
     這個檔案是專案範本系統的成品。 它可滿足 EmptyWeb.vstemplate 檔案中的專案檔案參考。  
  
### <a name="web-site-projects"></a>網站專案  
 這些檔案建立新的網站以回應**ASP.NET 網站**命令之後指向, 可供使用**新網站**上**檔案**功能表：  
  
-   Default.aspx  
  
     新的網站預設首頁。 Language 屬性會指定程式碼後置語言和 CodeFile 屬性會指定包含此頁面相關聯的程式碼後置程式碼的相依檔案。  
  
-   Default.aspx。*延伸模組*  
  
     包含預設首頁上的程式碼後置程式碼的相依檔案。 程式碼後置語言會決定*延伸*這個檔案。  
  
-   web.config  
  
     根 web.site 組態檔中。  
  
-   WebApplication.vstemplate  
  
     範本檔案，會決定網站方案的內容，並強制建立 App_Data 資料夾。  
  
-   WebApplication.webproj  
  
     這個檔案是專案範本系統的成品。 它可滿足 WebApplication.vstemplate 檔案中的專案檔案參考。  
  
### <a name="web-service-projects"></a>Web 服務專案  
 這些檔案建立新的網站以回應**ASP.NET Web 服務**命令，以指向之後可供使用**新網站**上**檔案**功能表：  
  
-   Service.asmx  
  
     新的 Web 服務的 HTML 頁面。 Language 屬性會指定程式碼後置語言和程式碼後置屬性會指定包含此服務相關聯的程式碼後置程式碼的相依檔案。  
  
-   服務。 *擴充功能*  
  
     服務類別會實作相依檔案。 程式碼後置語言會決定*延伸*這個檔案。  
  
-   web.config  
  
-   根 web.site 組態檔中。  
  
-   WebService.vstemplate  
  
     範本檔案，判斷網站方案的內容，並強制 App_Data 和 App_Code 資料夾的建立。 服務。*延伸*檔案複製到 App_Code 資料夾。  
  
-   WebService.webproj  
  
     這個檔案是專案範本系統的成品。 它可滿足 WebService.vstemplate 檔案中的專案檔案參考。  
  
## <a name="project-item-template-folder"></a>專案項目範本資料夾  
 Web 專案項目範本範本通常會安裝在 [*Visual Studio 安裝路徑*] \Common7\IDE\ItemTemplates\Web\\，其 web 程式設計語言所命名的子資料夾中的每個。  
  
## <a name="project-item-templates"></a>專案項目範本  
 網站專案項目範本用來將新的 Web 網頁加入至網站以回應**加入現有項目**命令。 目前支援這類的網頁：  
  
-   新的類別  
  
-   新的 HTML 網頁  
  
-   新的 Web Form  
  
-   新的主版頁面  
  
### <a name="new-class"></a>新的類別  
 此範本會建立新的來源檔案，定義空類別，以回應**加入新類別**命令。  
  
-   類別。 *擴充功能*  
  
     空的類別會實作原始程式檔。 程式碼後置語言會決定*延伸*這個檔案。  
  
-   Class.vstemplate  
  
     範本檔案，以建立原始程式檔，並判斷它的內容。  
  
### <a name="new-html-page"></a>新的 HTML 網頁  
 此範本建立新的網頁，以回應**加入新的 HTML 網頁**命令。  
  
-   HTMLPage.htm  
  
     起始網頁的內容。 這個 Web 網頁通常會有任何相關聯的程式碼後置相依檔案。 若要建立智慧頁面與相關聯的程式碼後置檔案，請改用 Web 表單範本。  
  
-   HTMLPage.vstemplate  
  
     範本檔案，建立網頁並判斷它的內容。  
  
### <a name="new-webform"></a>新 WebForm  
 此範本建立新的智慧網頁以回應**加入新的 Web Form**命令。  
  
 若要建立相依的程式碼後置原始程式檔，請選取**程式碼置於個別檔案**。 否則，會建立具有空的指令碼區塊，且沒有單一的 Web 網頁\<頁面 %%> 指示詞連結相依檔案。  
  
 若要建立選取的主版頁面的內容頁面，選取**選取的主版頁面**。  
  
-   WebForm.aspx  
  
     起始網頁的內容。 這個 Web 網頁會有任何相關聯的程式碼後置相依檔案。  
  
-   WebForm_cb.aspx  
  
     起始網頁的內容。 這個 Web 網頁會有相關聯的程式碼後置相依檔案。  
  
-   程式碼後置。 *擴充功能*  
  
     會實作 webform 類別相依檔案。 程式碼後置語言會決定*延伸*這個檔案。  
  
-   ContentPage.aspx  
  
     起始網頁做為內容頁面的內容。 這個 Web 網頁會有任何相關聯的程式碼後置相依檔案。  
  
-   ContentPage_cb.aspx  
  
     起始網頁做為內容頁面的內容。 這個 Web 網頁會有相關聯的程式碼後置相依檔案。  
  
-   WebForm.vstemplate  
  
     範本檔案會決定新的網頁和其相依檔案的內容，如果有的話。  
  
### <a name="new-master-page"></a>新的主版頁面  
 此範本建立新的主版頁面以回應**加入新的主版頁面**命令。  
  
 若要建立相依的程式碼後置原始程式檔，請選取**程式碼置於個別檔案**。 否則，會建立具有空的指令碼區塊，且沒有單一的 Web 網頁\<頁面 %%> 指示詞連結相依檔案。  
  
-   MasterPage.master  
  
     主版頁面的開始內容。 此主版頁面都有沒有相關聯的程式碼後置相依檔案。  
  
-   MasterPage_cb.master  
  
     主版頁面的開始內容。 此主版頁面都有相關聯的程式碼後置相依檔案。  
  
-   程式碼後置。*延伸模組*  
  
     主版頁面類別會實作相依檔案。 程式碼後置語言會決定*延伸*這個檔案。  
  
-   MasterPage.vstemplate  
  
     範本檔案會決定新的主版頁面和其相依檔案的內容，如果有的話。  
  
## <a name="see-also"></a>另請參閱  
 [網站支援](../../extensibility/internals/web-site-support.md)