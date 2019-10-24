---
title: Web 專案基本知識 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- web projects, essentials
ms.assetid: ca2f4e43-322c-4431-8680-52da846940bc
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5f3d3069d8cc539deeda7c9d44f8d1cbf27e8821
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72721666"
---
# <a name="web-project-essentials"></a>Web 專案的基本資訊
Web 專案會建立 Web 應用程式。 您可以使用 Web 專案來建立具有智慧型網頁的 Web 應用程式。 智慧型網頁具有伺服器端程式碼，可依需求呈現網頁。

 使用傳統的程式設計語言（例如 [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] 或 [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]），您可以建立智慧型網頁來收集和處理來自使用者的資訊、將其儲存在資料庫中等等。

- 程式碼後置模型會將相依的原始程式碼檔案與副檔名為 .aspx 或 .asmx 的網頁產生關聯。 例如，您的 hello .aspx 可能會有相依的原始程式碼檔 hello.aspx.cs。

- 與智慧網頁相關聯的伺服器端程式碼會編譯成可執行檔，此檔案位於網站/bin 資料夾中。

- 其他原始程式碼檔，例如與特定網頁沒有關聯的 helper 類別，則位於網站/App_Code 資料夾中。

  - 網站專案（WSP）會針對每個智慧型網頁產生一個可執行檔。 其他可執行檔是從/App_Code 資料夾中的任何原始程式碼檔案產生。

  - Web 應用程式專案（WAP）會產生單一可執行檔，其結合所有智慧型網頁的程式碼，以及/App_Code 資料夾中的所有原始程式檔。

- Web 專案的方案檔與網站本身分開。 根據預設，方案檔位於 \Documents 和 Settings \\*YourAccount*\My Documents \\ *\<Visual Studio # # # # >* \Projects \\*YourWebSite*。

  > [!NOTE]
  > 如果您想要將方案檔與網站保持在一起，請將它移至該處，然後重新開啟它。

- 如果您在 Visual Studio 中開啟沒有方案檔的網站，系統就會自動產生新的方案檔。

- Web 專案沒有任何專案檔。 專案資訊會儲存在方案檔、web.config 檔案和其他位置。

- 將全域屬性加入至 Web 專案時，會自動在 Web 專案方案資料夾中建立儲存檔案。

- 您可以使用 Page 指示詞或 \<script runat = "server" > 標記，將智慧型網頁與伺服器端程式設計語言產生關聯。

- 此外，網頁可以有任意數目的用戶端腳本區塊，以任何指令碼語言撰寫。

- 網站專案系統的執行方式，是將專案和專案範本和註冊加入至 [!INCLUDE[vwprvw](../../extensibility/internals/includes/vwprvw_md.md)] 專案。

- WAP 系統會實作為專案子類型，也稱為專案類別。 @No__t_0 專案是由 WAP 子類型 flavored，以建立 WAP 系統。 如需專案子類型的詳細資訊，請參閱[專案子類型](../../extensibility/internals/project-subtypes.md)。

- 智慧型網頁結合了 HTML 與伺服器端程式設計語言。 伺服器端語言稱為包含的語言。 為了支援包含的語言，Web 專案系統必須實作為 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> 系列的介面。

  - 為了在編輯器中支援包含的語言，HTML 語言服務必須延遲將內含的語言程式碼顯示為內含的語言服務。

  - 錯誤標記（紅色標示）應一律在程式碼編輯器的主要緩衝區中建立。

## <a name="see-also"></a>請參閱
- [Web 專案](../../extensibility/internals/web-projects.md)