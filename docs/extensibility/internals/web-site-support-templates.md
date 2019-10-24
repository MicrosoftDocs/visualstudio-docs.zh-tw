---
title: 網站支援範本 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- we site projects, templates
ms.assetid: 37173c97-486b-4b3c-8ed3-cf5890c4de23
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aceaa574fa2a0148236f033c610f8c53ca74e635
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72721593"
---
# <a name="web-site-support-templates"></a>網站支援範本
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 網站專案和專案範本提供可重複使用且可自訂的網站專案和專案存根，可讓您從頭開始建立新網站專案和專案的需求，以加速開發程式。 如需 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 範本的詳細資訊，請參閱[建立專案和專案範本](../../ide/creating-project-and-item-templates.md)。

## <a name="project-template-folder"></a>專案範本資料夾
 Web 專案範本通常會安裝在 [*Visual Studio 安裝路徑*] \Common7\IDE\ProjectTemplates\Web \\ 上，每個都位於以 Web 程式設計語言命名的子資料夾中。

## <a name="project-file"></a>專案檔
 @No__t_0 的整合式開發環境（IDE）需要專案副檔名做為將範本對應至正確專案類型的方式。 因為 Web 專案沒有專案檔，所以會註冊虛擬專案副檔名 .webproj，以將範本對應至專案類型。

 您可以選擇性地將語言名稱字串加入範本，讓 Web 專案系統針對以範本為基礎的專案，在 [**加入新專案**] 對話方塊中設定語言預設值。 此字串必須是檔案的第一行。 它必須符合 IntelliSense 引擎註冊中 AddItemLanguageName 下所註冊的名稱，以及在專案子類型（.Vstemplate）下註冊的名稱。 如需詳細資訊，請參閱[網站支援屬性](../../extensibility/internals/web-site-support-attributes.md)。

 如果字串不存在，Web 專案系統會根據專案範本新增至 Web 專案之頁面的語言屬性和副檔名，嘗試決定預設語言。

## <a name="project-templates"></a>專案範本
 網站專案範本是用來建立新的網站，以**回應 [檔案] 功能表上**的 [**新網站**] 命令。 目前支援三種網站專案類型：

- 空白網站專案

- 網站專案

- Web 服務專案

### <a name="empty-web-site-projects"></a>空白網站專案
 這些檔案會建立新的空白網站，以回應 [**空白網站**] 命令，**在選擇 [** 檔案]  >  [**新網站**] 之後即可使用：

- EmptyWeb .vstemplate

     範本檔案，可引導您建立新的空網站。

- EmptyWeb. .webproj

     此檔案是專案範本系統的成品。 它滿足 EmptyWeb 中的專案檔參考。

### <a name="web-site-projects"></a>網站專案
 這些檔案會建立新的網站以回應 [ **ASP.NET 網站**] 命令，**在選擇 [** 檔案]  >  [**新網站**] 之後，即可使用此命令：

- Default.aspx

     新網站的預設首頁。 Language 屬性會指定程式碼後置語言，而 CodeFile 屬性會指定包含與此頁面相關之程式碼後置的相依檔案。

- Default.aspx。*延伸*模組

     包含預設首頁之程式碼後置程式碼的相依檔案。 「後置語言」會決定此檔案的*副檔名*。

- web.config

     根網站設定檔。

- WebApplication .vstemplate

     範本檔案，可決定網站解決方案的內容，並強制建立 App_Data 資料夾。

- WebApplication. .webproj

     此檔案是專案範本系統的成品。 它滿足 WebApplication 中的專案檔參考。

### <a name="web-service-projects"></a>Web 服務專案
 這些檔案會建立新的網站，以回應**ASP.NET Web 服務**命令，**在選擇 [** 檔案] > [**新網站**] 之後，即可使用此命令：

- 服務 .asmx

     新 Web 服務的 HTML 頁面。 Language 屬性會指定程式碼後置語言，而後置屬性會指定包含與此服務相關聯之程式碼後置的相依檔案。

- 維護. *號*

     執行服務類別的相依檔案。 「後置語言」會決定此檔案的*副檔名*。

- web.config

- 根網站設定檔。

- WebService

     範本檔案，可決定網站解決方案的內容，並強制建立 App_Data 和 App_Code 資料夾。 服務。*擴充*檔案會複製到 App_Code 資料夾。

- WebService. .webproj

     此檔案是專案範本系統的成品。 它滿足 WebService .vstemplate 檔案中的專案檔參考。

## <a name="project-item-template-folder"></a>專案專案範本資料夾
 Web 專案-專案範本通常會安裝在 [*Visual Studio 安裝路徑*] \Common7\IDE\ItemTemplates\Web\\中，每個元件都在其 Web 程式語言所命名的子資料夾中。

## <a name="project-item-templates"></a>專案專案範本
 網站專案專案範本是用來將新網頁新增至網站，以回應 [**加入現有專案**] 命令。 目前支援這類網頁：

- 新增類別

- 新增 HTML 網頁

- 新的 Web 表單

- 新的主版頁面

### <a name="new-class"></a>新增類別
 此範本會建立新的原始程式檔，以定義空的類別以回應 [**加入新類別**] 命令。

- 類別。 *號*

     執行空類別的原始程式檔。 「後置語言」會決定此檔案的*副檔名*。

- 類別 .vstemplate

     建立原始程式檔並決定其內容的範本檔案。

### <a name="new-html-page"></a>新增 HTML 網頁
 此範本會建立新的網頁，以回應 [**加入新的 HTML 網頁**] 命令。

- Html 網頁 .htm

     網頁的起始內容。 此網頁通常沒有相關聯的程式碼後置相依檔案。 若要建立含有相關聯程式碼後置檔案的智慧頁面，請改用 Web 表單範本。

- Html 網頁 .vstemplate

     建立網頁並決定其內容的範本檔案。

### <a name="new-webform"></a>新增 WebForm
 此範本會建立新的智慧網頁，以回應 [**加入新的 Web 表單**] 命令。

 若要建立相依的程式碼後置來源檔案，請選取 **將程式碼放在不同的**檔案 否則，會建立具有空白腳本區塊的單一網頁，且不會有 \<% Page% > 指示詞連結相依的檔案。

 若要為選取的主版頁面建立內容頁，請選取 [**選取主版頁面**]。

- WebForm .aspx

     網頁的起始內容。 此網頁沒有相關聯的程式碼後置相依檔案。

- WebForm_cb .aspx

     網頁的起始內容。 此網頁有相關聯的程式碼後置相依檔案。

- 隱藏. *號*

     執行 webform 類別的相依檔案。 「後置語言」會決定此檔案的*副檔名*。

- ContentPage .aspx

     網頁的起始內容，做為內容頁面。 此網頁沒有相關聯的程式碼後置相依檔案。

- ContentPage_cb .aspx

     網頁的起始內容，做為內容頁面。 此網頁有相關聯的程式碼後置相依檔案。

- WebForm .vstemplate

     範本檔案，可決定新網頁及其相依檔案的內容（如果有的話）。

### <a name="new-master-page"></a>新的主版頁面
 此範本會建立新的主版頁面，以回應 [**加入新的主版頁面**] 命令。

 若要建立相依的程式碼後置來源檔案，請選取 **將程式碼放在不同的**檔案 否則，會建立具有空白腳本區塊的單一網頁，且不會有 \<% Page% > 指示詞連結相依的檔案。

- MasterPage master

     主版頁面的起始內容。 此主版頁面沒有相關聯的程式碼後置相依檔案。

- MasterPage_cb master

     主版頁面的起始內容。 此主版頁面具有相關聯的程式碼後置相依檔案。

- 隱藏.*延伸*模組

     執行主版頁面類別的相依檔案。 「後置語言」會決定此檔案的*副檔名*。

- MasterPage .vstemplate

     範本檔案，可決定新主版頁面及其相依檔案的內容（如果有的話）。

## <a name="see-also"></a>請參閱
- [網站支援](../../extensibility/internals/web-site-support.md)