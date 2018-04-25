---
title: Web 專案 Essentials |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- web projects, essentials
ms.assetid: ca2f4e43-322c-4431-8680-52da846940bc
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6918c539409a31dfe5249adb5858ca20c8c2337c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="web-project-essentials"></a>Web 專案的基本資訊
Web 專案建立 Web 應用程式。 您可以使用 Web 專案建立 Web 應用程式具有智慧網頁。 智慧網頁已呈現網頁上指定的伺服器端程式碼。  
  
 使用傳統的程式設計語言，例如[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]或[!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]，您可以建立智慧 Web 頁面，來收集和處理來自使用者的資訊、 將它儲存在資料庫中，等等。  
  
-   程式碼後置模型會將相依的原始程式檔與具有檔案副檔名.aspx 或.asmx 網頁產生關聯。 例如，hello.aspx 可能相依原始碼檔案 hello.aspx.cs。  
  
-   智慧網頁與相關聯的伺服器端程式碼會編譯到可執行檔位於網站 /bin 資料夾中。  
  
-   其他來源的程式碼檔案，例如未與特定網頁、 相關聯的 helper 類別位於網站 /App_Code 資料夾中。  
  
    -   網站專案 (WSP) 會產生一個可執行檔，每個智慧 Web 網頁。 其他可執行檔會產生從 /App_Code 資料夾中所有原始程式碼檔。  
  
    -   Web 應用程式專案 (WAP) 會產生單一的可執行檔，它結合了所有智慧網頁，以及 /App_Code 資料夾中的所有原始程式檔的程式碼。  
  
-   Web 專案的方案檔位於與網站本身分開。 根據預設，方案檔會位於 \Documents and 設定\\*YourAccount*\My 文件\\*\<Visual Studio # # # >* \Projects\\ *YourWebSite*。  
  
    > [!NOTE]
    >  如果您想要保留與網站的方案檔，只要那里移動，並重新開啟它。  
  
-   如果您開啟 Visual Studio 中沒有方案檔的網站時，新的方案檔會自動產生它。  
  
-   Web 專案的任何專案檔。 專案資訊會儲存在方案檔、 web.config 檔案中，和其他位置。  
  
-   自動加入至 Web 專案的全域屬性 Web 專案的方案資料夾中建立儲存體檔案。  
  
-   使用頁面指示詞，智慧網頁可以是相關聯的伺服器端程式設計語言或\<指令碼 runat ="server"> 標記。  
  
-   此外，網頁可以有任意任何的數目指令碼語言撰寫的用戶端指令碼區塊。  
  
-   網站專案系統藉由加入專案和項目範本，以及要註冊[!INCLUDE[vwprvw](../../extensibility/internals/includes/vwprvw_md.md)]專案。  
  
-   WAP 系統會實作為專案子類型，也稱為專案類別。 [!INCLUDE[vwprvw](../../extensibility/internals/includes/vwprvw_md.md)]專案已具備所建立 WAP 系統 WAP 子型別。 如需有關專案子類型的詳細資訊，請參閱[專案子類型](../../extensibility/internals/project-subtypes.md)。  
  
-   智慧網頁會結合伺服器端程式設計語言中的 HTML。 伺服器端語言稱為所包含的語言。 若要支援所包含的語言，Web 專案系統必須實作<xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage>系列的介面。  
  
    -   若要支援所包含的語言，在編輯器中，HTML 語言服務必須延後顯示包含的語言的程式碼所包含的語言服務。  
  
    -   一定要在程式碼編輯器的主要緩衝區中建立錯誤標記 （紅色曲線）。  
  
## <a name="see-also"></a>另請參閱  
 [Web 專案](../../extensibility/internals/web-projects.md)