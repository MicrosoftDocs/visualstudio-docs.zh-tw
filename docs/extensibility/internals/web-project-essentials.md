---
title: Web 專案的基本資訊 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- web projects, essentials
ms.assetid: ca2f4e43-322c-4431-8680-52da846940bc
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 30ffd684eb6527ee73e54cc590dc3e4b1d3c51d3
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63429345"
---
# <a name="web-project-essentials"></a>Web 專案的基本資訊
Web 專案建立 Web 應用程式。 您可以使用 Web 專案來建立智慧型 Web 網頁的 Web 應用程式。 智慧型的網頁上具有呈現網頁上，依需求的伺服器端程式碼。

 使用傳統的程式設計語言，例如[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]或[!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]，您可以建立智慧型 Web 頁面，來收集和處理來自使用者的資訊、 將它儲存在資料庫中，等等。

- 程式碼後置模型會將相依的原始程式碼檔案擁有.asmx 的檔案副檔名.aspx 網頁關聯。 比方說，hello.aspx 可能有相依的原始程式碼檔案 hello.aspx.cs。

- 智慧網頁相關聯的伺服器端程式碼會編譯為可執行檔位於網站的 /bin 資料夾中。

- 其他來源的程式碼檔案，例如與特定的網頁上，使用的協助程式類別位於網站 /App_Code 資料夾中。

  - 網站專案 (WSP) 會產生一個可執行檔，每個智慧的網頁。 從存放在 /App_Code 資料夾任何原始程式碼檔，會產生額外的可執行檔。

  - Web 應用程式專案 (WAP) 會產生單一的可執行檔的所有智慧網頁，以及在 /App_Code 資料夾中的所有原始程式檔中結合程式碼。

- Web 專案的方案檔位於與網站本身分開。 根據預設，方案檔會位於 \Documents and 設定\\*YourAccount*\My 文件\\*\<Visual Studio # # # >* \Projects\\ *YourWebSite*。

  > [!NOTE]
  > 如果您想要保留與網站的方案檔，只要那里移動，並重新開啟它。

- 如果您開啟 Visual Studio 中沒有方案檔的網站時，新的方案檔會自動產生它。

- Web 專案會有任何專案檔案。 專案資訊會儲存在方案檔、 web.config 檔案中，和其他位置。

- 將通用的屬性加入至 Web 專案會自動建立 Web 專案的方案資料夾中的儲存體檔案。

- 使用頁面指示詞，智慧型 Web 頁面可以是相關聯的伺服器端程式設計語言或\<指令碼 runat ="server"> 標記。

- 此外，網頁可以有任意任何的數目指令碼語言撰寫的用戶端指令碼區塊。

- 藉由加入專案和項目範本和註冊，以實作網站專案系統[!INCLUDE[vwprvw](../../extensibility/internals/includes/vwprvw_md.md)]專案。

- WAP 系統會實作為專案子類型，也稱為專案的類別。 [!INCLUDE[vwprvw](../../extensibility/internals/includes/vwprvw_md.md)]專案 WAP 子類型，來建立 WAP 系統的特色。 如需有關專案子類型的詳細資訊，請參閱[專案子類型](../../extensibility/internals/project-subtypes.md)。

- 智慧型的網頁會結合伺服器端程式設計語言中的 HTML。 伺服器端語言稱為自主的語言。 若要支援包含的語言，必須實作的 Web 專案系統<xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage>系列的介面。

  - 自主的語言支援在編輯器中，HTML 語言服務必須延後到自主的語言服務顯示包含的語言代碼。

  - 錯誤標記 （紅色曲線） 一定要建立程式碼編輯器的主要緩衝區中。

## <a name="see-also"></a>另請參閱
- [Web 專案](../../extensibility/internals/web-projects.md)