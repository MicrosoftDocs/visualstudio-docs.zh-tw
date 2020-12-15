---
title: 網站支援範本 |Microsoft Docs
description: 深入瞭解網站支援範本。 Visual Studio 的網站專案和專案範本提供可重複使用且可自訂的網站專案和專案存根。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- we site projects, templates
ms.assetid: 37173c97-486b-4b3c-8ed3-cf5890c4de23
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d7bb3d669dadf7c33fa81231adf26ae30e999c51
ms.sourcegitcommit: 19061b61759ce8e3b083a0e01a858e5435580b3e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/15/2020
ms.locfileid: "97487851"
---
# <a name="web-site-support-templates"></a>網站支援範本
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 網站專案和專案範本提供可重複使用且可自訂的網站專案和專案存根，可讓您從頭開始建立新的網站專案和專案的需求，以加速開發流程。 如需範本的詳細資訊 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ，請參閱 [建立專案和專案範本](../../ide/creating-project-and-item-templates.md)。

## <a name="project-template-folder"></a>專案範本資料夾
 Web 專案範本通常會安裝在 [*Visual Studio 安裝路徑*] \Common7\IDE\ProjectTemplates\Web 上 \\ ，每個都在以 Web 程式語言命名的子資料夾中。

## <a name="project-file"></a>專案檔
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]整合式開發環境 (IDE) 需要專案檔案副檔名，才能將範本對應至正確的專案類型。 因為 Web 專案沒有專案檔，所以會註冊虛擬專案副檔名 .webproj，以將範本對應至專案類型。

 您可以選擇性地將語言名稱字串加入至範本，讓 Web 專案系統在 [ **加入新專案** ] 對話方塊中，針對以範本為基礎的專案設定語言預設值。 字串必須是檔案的第一行。 它必須同時符合在 IntelliSense 引擎註冊的 AddItemLanguageName 下登錄的名稱，以及在專案子類型下註冊的名稱 (.Vstemplate) 。 如需詳細資訊，請參閱 [網站支援屬性](../../extensibility/internals/web-site-support-attributes.md)。

 如果字串不存在，Web 專案系統會根據專案範本新增至 Web 專案之頁面的語言屬性和副檔名，來決定預設語言。

## <a name="project-templates"></a>專案範本
 網站專案範本可用來建立新的 **網站，以** 回應 [檔案] 功能表上的 [**新網站**] 命令。 目前支援的網站專案類型有三種：

- 空白網站專案

- 網站專案

- Web 服務專案

### <a name="empty-web-site-projects"></a>空白網站專案
 這些檔案會建立新的空白網站，以回應 [**空白網站**] 命令（**在選擇 [** 檔案新網站] 之後可用）  >  ****：

- EmptyWeb .vstemplate

     此範本檔案會引導您建立新的空網站。

- EmptyWeb. .webproj

     這個檔案是專案範本系統的成品。 它滿足 EmptyWeb .vstemplate 檔案中的專案檔參考。

### <a name="web-site-projects"></a>網站專案
 這些檔案會建立新的網站，以回應 [ **ASP.NET 網站**] 命令，**在選擇 [** 檔案  >  **新增網站**] 之後可使用此命令：

- Default.aspx

     新網站的預設首頁。 Language 屬性會指定程式碼後置語言，而 CodeFile 屬性則會指定相依檔案，其中包含與此頁面相關聯的程式碼後置程式碼。

- Default.aspx。*延伸* 模組

     相依檔案，其中包含預設首頁的程式碼後置程式碼。 程式碼後置語言會決定這個檔案的 *副檔名* 。

- web.config

     根網站設定檔案。

- WebApplication .vstemplate

     此範本檔案可判斷網站解決方案的內容，並強制建立 App_Data 資料夾。

- WebApplication. .webproj

     這個檔案是專案範本系統的成品。 它滿足 WebApplication .vstemplate 檔案中的專案檔參考。

### <a name="web-service-projects"></a>Web 服務專案
 這些檔案會 **建立新的** 網站，以回應 **ASP.NET Web 服務** 命令，在選擇 [檔案  >  **新網站**] 之後可用：

- .Asmx

     新 Web 服務的 HTML 頁面。 Language 屬性會指定程式碼後置語言，而程式碼後置屬性則會指定相依檔案，其中包含與此服務相關聯的程式碼後置程式碼。

- 服務。 *擴充功能*

     實作為服務類別的相依檔案。 程式碼後置語言會決定這個檔案的 *副檔名* 。

- web.config

- 根網站設定檔案。

- WebService

     此範本檔案會決定網站解決方案的內容，並強制建立 App_Data 和 App_Code 資料夾。 服務。*擴充* 檔會複製到 App_Code 資料夾。

- Web .webproj

     這個檔案是專案範本系統的成品。 它滿足 WebService 檔案中的專案檔參考。

## <a name="project-item-template-folder"></a>專案專案範本資料夾
 Web 專案專案範本通常會安裝在 [*Visual Studio 安裝路徑*] \Common7\IDE\ItemTemplates\Web 中 \\ ，每個都在以其 Web 程式設計語言命名的子資料夾中。

## <a name="project-item-templates"></a>專案專案範本
 網站專案專案範本可用來將網頁新增至網站，以回應 [ **加入現有專案** ] 命令。 目前支援這類網頁：

- 新增類別

- 新的 HTML 網頁

- 新的 Web 表單

- 新增主版頁面

### <a name="new-class"></a>新增類別
 此範本會建立新的原始程式檔，以定義空類別以回應 [ **加入新類別** ] 命令。

- 類別。 *擴充功能*

     實作為空類別的原始程式檔。 程式碼後置語言會決定這個檔案的 *副檔名* 。

- 類別 .vstemplate

     建立原始程式檔並決定其內容的範本檔案。

### <a name="new-html-page"></a>新的 HTML 網頁
 此範本會建立新的網頁，以回應 [ **加入新的 HTML 網頁** ] 命令。

- HTMLPage.htm

     網頁的開始內容。 此網頁通常沒有相關聯的程式碼後置相依檔案。 若要使用相關聯的程式碼後置檔案來建立智慧型頁面，請改用 Web Form 範本。

- Html 網頁 .vstemplate

     建立網頁並決定其內容的範本檔案。

### <a name="new-webform"></a>新 WebForm
 此範本會建立新的智慧型網頁，以回應 [ **加入新的 Web 表單** ] 命令。

 若要建立相依的程式碼後置原始程式檔，請選取 [ **將程式碼放在個別** 檔案 否則，會建立具有空白腳本區塊的單一網頁，而不會有指示詞 \<% Page %> 來連結相依的檔案。

 若要為選取的主版頁面建立內容頁面，請選取 [ **選取主版頁面**]。

- WebForm .aspx

     網頁的開始內容。 此網頁沒有相關聯的程式碼後置相依檔案。

- WebForm_cb .aspx

     網頁的開始內容。 此網頁有相關聯的程式碼後置相依檔案。

- Codebehind. *擴充功能*

     實 webform 類別的相依檔案。 程式碼後置語言會決定這個檔案的 *副檔名* 。

- ContentPage .aspx

     作為內容頁面之網頁的開始內容。 此網頁沒有相關聯的程式碼後置相依檔案。

- ContentPage_cb .aspx

     作為內容頁面之網頁的開始內容。 此網頁有相關聯的程式碼後置相依檔案。

- WebForm .vstemplate

     此範本檔案會決定新網頁的內容及其相依檔案（如果有的話）。

### <a name="new-master-page"></a>新增主版頁面
 此範本會建立新的主版頁面，以回應 [新增 **主版頁面** ] 命令。

 若要建立相依的程式碼後置原始程式檔，請選取 [ **將程式碼放在個別** 檔案 否則，會建立具有空白腳本區塊的單一網頁，而不會有指示詞 \<% Page %> 來連結相依的檔案。

- MasterPage master

     主版頁面的開始內容。 此主版頁面沒有相關聯的程式碼後置相依檔案。

- MasterPage_cb master

     主版頁面的開始內容。 此主版頁面有相關聯的程式碼後置相依檔案。

- Codebehind.*延伸* 模組

     執行主版頁面類別的相依檔案。 程式碼後置語言會決定這個檔案的 *副檔名* 。

- MasterPage .vstemplate

     此範本檔案會決定新主版頁面及其相依檔案的內容（如果有的話）。

## <a name="see-also"></a>另請參閱
- [網站支援](../../extensibility/internals/web-site-support.md)
