---
title: 網站支援範本 |微軟文件
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
ms.openlocfilehash: 0e3c139ae6f2f9ec618e6382a1551a9e35eee7ec
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703458"
---
# <a name="web-site-support-templates"></a>網站支援範本
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]網站專案和專案範本提供可重用和可自定義的網站專案和專案存根,透過消除從頭開始創建新網站專案和專案的需求來加快開發過程。 有關[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]樣本的詳細資訊,請參閱[建立項目和專案範本](../../ide/creating-project-and-item-templates.md)。

## <a name="project-template-folder"></a>專案樣本資料夾
 Web 專案樣本通常安裝在 [*可視化工作室安裝路徑*][公共\\7_IDE_ProjectTemplates]Web 上,每個範本都位於以 Web 程式設計語言命名的子資料夾中。

## <a name="project-file"></a>專案檔
 集成[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]開發環境 (IDE) 需要專案檔副檔名作為將範本映射到正確專案類型的一種方式。 由於 Web 專案沒有專案檔,因此註冊了虛擬專案檔擴展名 .webproj 以將範本映射到專案類型。

 或者,可以將語言名稱字串添加到範本中,以使 Web 專案系統能夠根據樣本為專案在「**添加新專案」** 對話方塊中設定語言預設值。 字串必須是檔的第一行。 它必須與 IntelliSense 引擎註冊中在 AddItem 語言名稱下註冊的名稱和在專案子類型(VsTemplate)下註冊的名稱相匹配。 有關詳細資訊,請參閱[網站支援屬性](../../extensibility/internals/web-site-support-attributes.md)。

 如果字串不存在,Web 專案系統將嘗試根據專案範本添加到 Web 專案的頁面的語言屬性和檔副檔名來確定預設語言。

## <a name="project-templates"></a>專案範本
 網站項目範本用於生成新網站以回應 **「檔**」功能表上**的「新建網站」** 命令。 目前支援三種網站項目類型:

- 空網站專案

- 網站專案

- Web 服務專案

### <a name="empty-web-site-projects"></a>空網站專案
 這些檔案建立新的空網站,以回應**空網站**命令,此命令在選擇 **「檔案** > **新網站**」後可用:

- 剩餘Web.vstemplate

     指導創建新空網站的範本檔。

- 空Web.webproj

     此檔是專案範本系統的專案。 它滿足 EmptyWeb.vstemplate 檔案中的專案檔引用。

### <a name="web-site-projects"></a>網站專案
 這些檔案建立新的網站,以回應**ASP.NET 網站**指令,該指令在選擇 **「檔案** > **新網站**」後可用:

- Default.aspx

     新網站的預設主頁。 語言屬性指定代碼背後語言,CodeFile 屬性指定包含與此頁面關聯的代碼後面的從屬檔。

- 默認值.aspx。*延伸*

     包含預設主頁的代碼後面代碼的從屬檔。 程式碼背後語言確定此檔案的*副檔名*。

- web.config

     根網站配置檔。

- Web應用程式.vstemplate

     範本檔,用於確定網站解決方案的內容並強制創建App_Data資料夾。

- Web應用程式.webproj

     此檔是專案範本系統的專案。 它滿足 WebApplication.vstemplate 檔案中的專案檔引用。

### <a name="web-service-projects"></a>Web 服務專案
 這些檔案建立新的網站,以回應**ASP.NET Web 服務**命令,該命令在選擇 **「檔案** > **新網站**」後可用:

- 服務.asmx

     新 Web 服務的 HTML 頁。 語言屬性指定代碼背後語言,Code背後屬性指定包含與此服務關聯的代碼後面的從屬檔。

- 服務。 *延伸*

     實現服務類的從屬檔。 程式碼背後語言確定此檔案的*副檔名*。

- web.config

- 根網站配置檔。

- WebService.vstemplate

     範本檔,用於確定網站解決方案的內容並強制創建App_Data和App_Code資料夾。 服務。*擴展檔案*將複製到App_Code資料夾。

- WebService.webproj

     此檔是專案範本系統的專案。 它滿足 WebService.vstemplate 檔案中的專案檔引用。

## <a name="project-item-template-folder"></a>專案樣本資料夾
 Web 專案項目樣本通常安裝在[*可視化工作室安裝路徑*] [公共\\7_IDE_ItemTemplates]Web 中,每個範本都位於以 Web 程式設計語言命名的子資料夾中。

## <a name="project-item-templates"></a>專案專案範本
 網站項目專案範本用於向網站添加新網頁以回應 **「添加現有專案」** 命令。 目前支援這些類型的網頁:

- 新類

- 新的 HTML 頁面

- 新 Web 表單

- 新母版頁

### <a name="new-class"></a>新類
 此範本建立一個新的源檔,用於定義一個空類以回應 **「添加新類」** 命令。

- 類別。 *延伸*

     實現空類的源檔。 程式碼背後語言確定此檔案的*副檔名*。

- 類別.vstemplate

     建立源檔並確定其內容的範本檔。

### <a name="new-html-page"></a>新的 HTML 頁面
 此範本建立新網頁以回應 **「新增新 HTML 頁」** 命令。

- HTMLPage.htm

     網頁的起始內容。 此網頁通常沒有關聯的代碼背後的從屬檔。 要使用關聯的代碼背後檔創建智能頁面,請使用 Web 窗體範本。

- HTMLPage.vstemplate

     創建網頁並確定其內容的範本檔。

### <a name="new-webform"></a>新 Web 表單
 此範本建立新的智慧網頁以回應 **「添加新 Web 窗體」** 命令。

 要建立來源檔的從屬代碼,請選擇**將代碼放在單獨的檔案中**。 否則,將創建一個 Web 頁,該網頁具有空腳\<本塊 ,並且沒有 %Page %> 指令來掛接從屬檔。

 要為選取母版頁創建內容頁,請選擇 **「選擇母版頁**」 。。

- WebForm.aspx

     網頁的起始內容。 此網頁沒有關聯的代碼背後的從屬檔。

- WebForm_cb.aspx

     網頁的起始內容。 此網頁具有關聯的代碼背後相關文件。

- 代碼後面。 *延伸*

     實現 Webform 類別的從屬檔。 程式碼背後語言確定此檔案的*副檔名*。

- 內容頁.aspx

     網頁的起始內容作為內容頁。 此網頁沒有關聯的代碼背後的從屬檔。

- ContentPage_cb.aspx

     網頁的起始內容作為內容頁。 此網頁具有關聯的代碼背後相關文件。

- WebForm.vstemplate

     確定新網頁及其從屬檔(如果有)內容的範本檔。

### <a name="new-master-page"></a>新母版頁
 此範本建立一個新的母版頁以回應 **「添加新母版頁」** 命令。

 要建立來源檔的從屬代碼,請選擇**將代碼放在單獨的檔案中**。 否則,將創建一個 Web 頁,該網頁具有空\<腳本塊,並且沒有 %Page %> 指令來掛接從屬檔。

- 母版

     母版頁的起始內容。 此母版頁沒有關聯的代碼背後的從屬檔。

- MasterPage_cb.master

     母版頁的起始內容。 此母版頁具有關聯的代碼背後從屬檔。

- 代碼後面。*延伸*

     實現母版頁類的從屬檔。 程式碼背後語言確定此檔案的*副檔名*。

- 母版頁面.vstemplate

     確定新母版頁及其從屬檔(如果有)內容的範本檔。

## <a name="see-also"></a>另請參閱
- [網站支援](../../extensibility/internals/web-site-support.md)
