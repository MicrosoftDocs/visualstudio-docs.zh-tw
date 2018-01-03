---
title: "登錄 .NET Framework 的擴充功能 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Add References dialog box, registering extensions of the .NET Framework
- MSBuild, registering extensions of the .NET Framework
- .NET Framework extensions, registering
ms.assetid: deee6f53-ea87-4b88-a120-bea589822e03
caps.latest.revision: "5"
author: kempb
ms.author: kempb
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: 5e9ab37b054dd137590b38dcd62d2de7ebdd1cd1
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="registering-extensions-of-the-net-framework"></a>註冊 .NET Framework 的擴充功能
您可以開發組件來擴充特定版本的 .NET Framework。 若要讓組件出現在 Visual Studio 的 [加入參考] 對話方塊中，您必須將包含該組件的資料夾加入至系統登錄。  
  
 例如，假設 Trey Research 公司所開發的程式庫會擴充 .NET Framework 4，並想讓程式庫組件在專案以 .NET Framework 4 為目標時出現在 [加入參考] 對話方塊中。 此外，假設組件是在 32 位元電腦上執行的 32 位元組件或 64 位元電腦上執行的 64 位元組件，而且它們將安裝於 C:\TreyResearch\Extensions4\ 資料夾中。  
  
 使用下列機碼來登錄此資料夾：HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework\v4.0.21006\AssemblyFoldersEx\TreyResearch\\。 為機碼提供此預設值︰C:\TreyResearch\Extensions4。  
  
> [!NOTE]
>  .NET Framework 版本的組建編號可能不同。  
  
 若要登錄 64 位元電腦上的 32 位元組件，請使用 Wow6432 節點，例如︰HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework\v4.0.21006\AssemblyFoldersEx\TreyResearch\\。  
  
## <a name="see-also"></a>請參閱  
 [Visual Studio 整合](../msbuild/visual-studio-integration-msbuild.md)