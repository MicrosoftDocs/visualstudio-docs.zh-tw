---
title: 選項對話方塊、專案和方案、組建和執行
description: '指定可以同時建立的 c + + 或 c # 專案最大數目、特定的預設組建行為，以及 Visual Studio 中的某些組建記錄檔設定。'
'\ms.custom': SEO-VS-2020
ms.date: 07/14/2017
ms.technology: vs-ide-compile
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Projects.Build_and_Run
helpviewer_keywords:
- builds [Visual Studio], setting up
- run actions
- debugger, run options
ms.assetid: c884976e-c0df-4c6d-8e3a-856ea2bd547c
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f3b6d98e715d0c86af6948f2fcc502e94dfde56a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99910831"
---
# <a name="options-dialog-box-projects-and-solutions--build-and-run"></a>選項對話方塊： \> 建立和執行專案和方案

在此對話方塊中，您可以指定可同時建置的 C++ 或 C# 專案最大數目、特定的預設建置行為，和一些建置記錄檔設定。 若要存取這些選項，請選取 [**工具**  >  **選項**] 展開 [**專案和方案**]，然後選取 [**建立並執行**]。

**平行專案組建的最大數目**

指定可同時建置的 C++ 和 C# 專案的最大數目。 若要最佳化建置程序，平行專案組建的最大數目會自動設定為您電腦的 CPU 數目。 最大值為 32。

**僅在執行時建置啟始專案和相依性**

當您使用 **F5** 鍵、[偵錯] > [開始偵錯] 功能表命令，或 [建置] 功能表上的適用命令時，只會建置啟始檔案及其相依性。 如果已取消選取，就會建置所有專案和相依性。

**執行時 (當專案過期時)**

*只適用於 C++ 專案。*

以 **F5** 或 [偵錯] > [開始偵錯] 命令執行專案時，如果專案設定已過期，預設設定 [提示建置] 會顯示訊息。 選取 [一律建置]，則每次執行專案時都會建置專案。 選取 [永不建置] 會在專案執行時隱藏所有自動建置。

**執行時 (當發生建置或部署錯誤時)**

*只適用於 C++ 專案。*

以 **F5** 或 [偵錯] > [開始偵錯] 命令執行專案時，如果即使建置失敗也應執行專案，預設設定 [提示啟動] 會顯示訊息。 選取 [啟動舊版本] 會自動啟動最後的良好組建，但可能會導致執行的程式碼和原始程式碼之間不相符。 選取 [不啟動] 來隱藏訊息。

**對新解決方案使用目前選取的專案作為啟始專案**

設定此選項時，新解決方案會使用目前選取的專案作為啟始專案。

**MSBuild 專案組建輸出詳細資訊**

決定要在 [輸出] 視窗中顯示多少建置流程的資訊。

**MSBuild 專案組建記錄檔詳細資訊**

*只適用於 C++ 專案。*

決定要將多少資訊寫入組建記錄檔（位於 *\\ \<ProjectName> \Debug \\ \<ProjectName>*）。

## <a name="see-also"></a>另請參閱

- [編譯和建置](../../ide/compiling-and-building-in-visual-studio.md)
- [選項對話方塊、專案和方案](projects-and-solutions-options-dialog-box.md)
- [選項對話方塊、專案和方案、Web 專案](options-dialog-box-projects-and-solutions-web-projects.md)