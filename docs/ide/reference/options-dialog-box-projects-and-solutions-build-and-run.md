---
title: "選項對話方塊、專案和解決方案、建置並執行 | Microsoft Docs"
ms.custom: 
ms.date: 07/14/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Projects.Build_and_Run
- VS.ToolsOptionsPag.Projects.Build_and_Run
helpviewer_keywords:
- builds [Visual Studio], setting up
- run actions
- debugger, run options
ms.assetid: c884976e-c0df-4c6d-8e3a-856ea2bd547c
caps.latest.revision: "20"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e15880551e2a896bca473d463b253ec15dda7b36
ms.sourcegitcommit: c0422a3d594ea5ae8fc03f1aee684b04f417522e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/02/2017
---
# <a name="options-dialog-box--projects-and-solutions-build-and-run"></a>選項對話方塊, 專案和方案, 建置和執行

在此對話方塊中，您可以指定可同時建置的 Visual C++ 或 Visual C# 專案最大數目、特定的預設建置行為，和一些建置記錄檔設定。 若要存取這些選項，請選取 [工具] > [選項] 來展開 [專案和方案]，然後選取 [建置並執行]。
  
**平行專案組建的最大數目**  
指定可同時建置的 Visual C++ 和 Visual C# 專案的最大數目。 若要最佳化建置程序，平行專案組建的最大數目會自動設定為您電腦的 CPU 數目。 最大值是 32。  

**僅在執行時建置啟始專案和相依性**  
當您使用 F5 鍵，再選取 [偵錯] > [開始] 功能表命令，或使用 [建置] 功能表上的適用命令時，只會建置啟始檔案及其相依性。 如果清除，就會建置所有專案和相依性。 

**執行時 (當專案過期時)**  
*只適用於 [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] 專案。*

以 F5 或 [偵錯] > [啟動] 命令執行專案時，如果專案設定已過期，預設設定 [提示建置] 會顯示訊息。 選取 [一律建置]，則每次執行專案時都會建置專案。 選取 [永不建置] 會在專案執行時隱藏所有自動建置。

**執行時 (當發生建置或部署錯誤時)**  
*只適用於 [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] 專案。*

以 F5 或 [偵錯] > [開始] 命令執行專案時，如果即使建置失敗也應執行專案，預設設定 [提示啟動] 會顯示訊息。 選取 [啟動舊版本] 會自動啟動最後的良好組建，但可能會導致執行的程式碼和原始程式碼之間不相符。 選取 [不啟動] 來隱藏訊息。

**對新解決方案使用目前選取的專案作為啟始專案**  
設定此選項時，新解決方案會使用目前選取的專案作為啟始專案。  

**MSBuild 專案組建輸出詳細資訊**  
決定建置的 [輸出] 視窗顯示多少資訊。  

**MSBuild 專案組建記錄檔詳細資訊**  
*只適用於 [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] 專案。*

決定多少資訊會寫入建置記錄檔，其位置在 \\...\\*專案名稱*\Debug\\*專案名稱*.log。  

## <a name="see-also"></a>請參閱  
[編譯和建置](../../ide/compiling-and-building-in-visual-studio.md)  
[選項對話方塊、專案和方案](projects-and-solutions-options-dialog-box.md)  
[選項對話方塊、專案和方案、Web 專案](options-dialog-box-projects-and-solutions-web-projects.md)