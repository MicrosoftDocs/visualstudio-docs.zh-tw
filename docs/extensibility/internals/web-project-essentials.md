---
title: Web 專案基本概念 |Microsoft Docs
description: 瞭解 Web 專案如何在 Visual Studio 中運作的內部詳細資料。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- web projects, essentials
ms.assetid: ca2f4e43-322c-4431-8680-52da846940bc
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 9442dcdd460e1213c3c07ee87a5ea2e0d7099072
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105085698"
---
# <a name="web-project-essentials"></a>Web 專案的基本資訊
Web 專案會建立 Web 應用程式。 您可以使用 Web 專案建立具有智慧型網頁的 Web 應用程式。 智慧型網頁具有可隨選轉譯網頁的伺服器端程式碼。

 使用傳統的程式設計語言（例如 [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] 或 [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] ），您可以建立智慧型網頁來收集和處理使用者的資訊，將資訊儲存在資料庫中等等。

- 程式碼後端模型會將相依原始程式碼檔與副檔名為 .aspx 或 .asmx 的網頁產生關聯。 例如，default.aspx 可能會有相依的原始程式碼檔 .aspx. .cs。

- 與智慧網頁相關聯的伺服器端程式碼會編譯成位於網站/bin 資料夾中的可執行檔。

- 其他原始程式碼檔（例如與特定網頁沒有關聯的 helper 類別）位於網站/App_Code 資料夾中。

  -  (WSP) 的網站專案會為每個智慧型網頁產生一個可執行檔。 其他可執行檔是從/App_Code 資料夾中的任何原始程式碼檔產生。

  -  (WAP) 的 Web 應用程式專案會產生單一可執行檔，結合所有智慧型網頁的程式碼，以及/App_Code 資料夾中的所有原始程式檔。

- Web 專案的方案檔是與網站本身分開定位。 根據預設，解決方案檔位於 \Documents and Settings \\ *您帳戶*\My Documents \\ *\<Visual Studio ####>* \Projects \\ *YourWebSite*。

  > [!NOTE]
  > 如果您想要將方案檔與網站保持在一起，只要將它移到該處，然後重新開啟即可。

- 如果您在 Visual Studio 中開啟沒有方案檔的網站，則會自動產生新的方案檔。

- Web 專案沒有任何專案檔。 專案資訊儲存在方案檔、web.config 檔案和其他位置。

- 將全域屬性加入至 Web 專案時，會自動在 Web 專案方案資料夾中建立儲存體檔案。

- 您可以使用 Page 指示詞或標記，將智慧型網頁與伺服器端程式設計語言相關聯 \<script runat="server"> 。

- 此外，Web pages 可以有任意數目的用戶端腳本區塊，以任何指令碼語言撰寫。

- 網站專案系統是藉由將專案和專案範本和註冊新增至專案來執行 [!INCLUDE[vwprvw](../../extensibility/internals/includes/vwprvw_md.md)] 。

- WAP 系統會實作為專案子類型，也稱為專案類別。 [!INCLUDE[vwprvw](../../extensibility/internals/includes/vwprvw_md.md)]Wap 子類型會 flavored 專案，以建立 wap 系統。 如需專案子類型的詳細資訊，請參閱 [專案子類型](../../extensibility/internals/project-subtypes.md)。

- 智慧型網頁結合了 HTML 與伺服器端程式設計語言。 伺服器端語言稱為「包含的語言」。 為了支援包含的語言，Web 專案系統必須執行 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> 介面系列。

  - 為了在編輯器中支援包含的語言，HTML 語言服務必須延後將內含的語言程式碼顯示為內含語言服務。

  - 錯誤標記 (red 標記) 應該一律在程式碼編輯器的主要緩衝區中建立。

## <a name="see-also"></a>另請參閱
- [Web 專案](../../extensibility/internals/web-projects.md)
