---
title: 網路項目要點 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- web projects, essentials
ms.assetid: ca2f4e43-322c-4431-8680-52da846940bc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 09e33248ca264fefa79a8d5d5fa5d0cfa3d2da1d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703542"
---
# <a name="web-project-essentials"></a>Web 專案的基本資訊
Web 專案創建 Web 應用程式。 可以使用 Web 專案建立具有智慧 Web 頁的 Web 應用程式。 智慧網頁具有伺服器端代碼,可按需呈現該網頁。

 使用傳統的程式設計語言(如[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]或[!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)])可以創建智慧網頁來收集和處理使用者的資訊,將其存儲在資料庫中,等等。

- 代碼後面模型將相關的原始程式碼檔與具有文件副檔名 .aspx 或 .asmx 的網頁關聯。 例如,hello.aspx 可能具有從屬原始程式碼檔hello.aspx.cs。

- 與智慧 Web 頁關聯的伺服器端代碼將編譯為位於網站/ bin 資料夾中的可執行檔。

- 其他原始碼檔(如未與特定網頁關聯的幫助程式類)位於網站 /App_Code資料夾中。

  - 網站專案 (WSP) 為每個智慧網頁生成一個可執行檔。 其他可執行檔從 /App_Code 資料夾中的任何原始程式碼檔生成。

  - Web 應用程式專案 (WAP) 生成單個可執行檔,該檔結合了所有智慧 Web 頁以及 /App_Code 資料夾中的所有源檔的代碼。

- Web 專案的解決方案檔與網站本身分開。 預設情況下,解決方案檔案位於 [文件和\\設定*您的帳戶*]\\我的文檔*\<視覺化工作室 [>*[專案\\*您的網站*。

  > [!NOTE]
  > 如果要將解決方案檔保留到 Web 網站中,只需將其移到該網站並重新打開它。

- 如果打開 Visual Studio 中沒有解決方案檔的網站,將自動為其生成新的解決方案檔。

- Web 專案沒有項目檔。 專案資訊存儲在解決方案檔、Web.config 檔案和其他地方。

- 將全域屬性添加到 Web 專案會自動在 Web 專案解決方案資料夾中創建儲存檔案。

- 通過使用 Page 指令或腳本 runat_"server">标记,\<智慧 Web 頁可以與伺服器端程式設計語言相關聯。

- 此外,網頁可以用任何腳本語言編寫任意數量的用戶端腳本塊。

- 通過將專案和專案樣本以及註冊添加到專案,[!INCLUDE[vwprvw](../../extensibility/internals/includes/vwprvw_md.md)]實現了網站專案系統。

- WAP 系統作為專案子類型實現,也稱為項目風格。 專案[!INCLUDE[vwprvw](../../extensibility/internals/includes/vwprvw_md.md)]由 WAP 子類型調味以創建 WAP 系統。 有關項目子型態的詳細資訊,請參考[專案子型態](../../extensibility/internals/project-subtypes.md)。

- 智慧網頁將 HTML 與伺服器端程式設計語言相結合。 伺服器端語言稱為包含語言。 為了支援包含的語言,Web 專案系統必須實現<xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage>介面的系列。

  - 要支援編輯器中包含的語言,HTML 語言服務必須將顯示包含的語言代碼推遲到包含的語言服務。

  - 錯誤標記(紅色波浪)應始終在代碼編輯器的主緩衝區中創建。

## <a name="see-also"></a>另請參閱
- [Web 專案](../../extensibility/internals/web-projects.md)
