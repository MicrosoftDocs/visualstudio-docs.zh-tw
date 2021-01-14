---
title: Web 專案的屬性設定 |Microsoft Docs
description: 瞭解如何在 Visual Studio 的 [屬性頁] 對話方塊中，變更網站偵錯工具的屬性設定。
ms.custom: SEO-VS-2020, seodec18
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], Web applications
- project settings [Visual Studio], debug configurations
- debug builds, project settings
- projects [Visual Studio], debug configurations
- debugging Web applications, project settings
- debug configurations, Web projects
ms.assetid: 8ec5160a-6408-4f47-8d41-f0e20e79a3b9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 86f15a6fa622bf7938740111705a295e09f3e443
ms.sourcegitcommit: a436ba564717b992eb1984b28ea0aec801eacaec
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/14/2021
ms.locfileid: "98205550"
---
# <a name="property-pages-settings-for-web-projects"></a>Web 專案的屬性頁設定
您可以在 [屬性頁] 對話方塊中使用[偵錯和發行組態](../debugger/how-to-set-debug-and-release-configurations.md)中所討論的方法，變更網站偵錯組態的屬性設定。 下表顯示 [屬性頁] 對話方塊中與偵錯工具相關的設定位置。

### <a name="start-options-category"></a>開始選項分類

| **設定** | **說明** |
| - | - |
| **啟動執行** | 標題，用以分類與應用程式啟動相關的選項。 |
| **使用目前的頁面** | 指定目前的頁面為偵錯的起始點。 |
| **特定的頁面：** | 指定您要開始偵錯的網頁。 |
| **啟動外部程式：** | 指定用來啟動您要偵錯的應用程式之命令。 |
| **命令列引數：** | 指定上述指定命令的引數。 |
| **工作目錄：** | 指定為程式偵錯時的工作目錄。 在 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] 中，工作目錄預設為啟動應用程式的來源目錄：\bin\debug。 |
| **起始 URL** | 指定您要偵錯的 Web 應用程式之位置。 |
| **不要開啟頁面。等候來自外部應用程式的要求** | 等候來自外部應用程式的要求。 這個選項不會啟動 Internet Explorer 或其他應用程式。 只會在應用程式呼叫時準備進行偵錯。 |
| **伺服器** | 標題，用以分類與使用的伺服器相關的選項。 |
| **使用預設網頁伺服器** | 使用預設的 Web 伺服器。 |
| **使用自訂伺服器** | 允許您輸入基礎 URL 用以做為伺服器。 |
| **偵錯工具** | 標題，用以分類與要進行之偵錯類型相關的選項。 |
| **ASP.NET 偵錯** | 啟用為 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 開發平台所撰寫的伺服器頁面偵錯。 您必須在 [起始 URL] 中指定 URL。 |
| **機器碼偵錯** | 讓您可以從 Managed 應用程式偵錯原生 (Unmanaged) Win32 程式碼的呼叫。 |
| **SQL Server 偵錯** | 允許 SQL Server 資料庫物件偵錯。 |
| **Silverlight 調試** | 允許偵錯 Silverlight 元件。 |

## <a name="see-also"></a>請參閱
- [偵錯工具設定和準備](../debugger/debugger-settings-and-preparation.md)