---
title: 登錄 .NET Framework 的擴充功能 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- Add References dialog box, registering extensions of the .NET Framework
- MSBuild, registering extensions of the .NET Framework
- .NET Framework extensions, registering
ms.assetid: deee6f53-ea87-4b88-a120-bea589822e03
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a5963faa5acb72ab0c94ca6b346456d83276e361
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63445237"
---
# <a name="registering-extensions-of-the-net-framework"></a>註冊 .NET Framework 的擴充功能
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以開發組件來擴充特定版本的 .NET Framework。 若要讓組件出現在 Visual Studio 的 [加入參考] 對話方塊中，您必須將包含該組件的資料夾加入至系統登錄。  
  
 例如，假設 Trey Research 公司所開發的程式庫會擴充 .NET Framework 4，並想讓程式庫組件在專案以 .NET Framework 4 為目標時出現在 [加入參考] 對話方塊中。 此外，假設組件是在 32 位元電腦上執行的 32 位元組件或 64 位元電腦上執行的 64 位元組件，而且它們將安裝於 C:\TreyResearch\Extensions4\ 資料夾中。  
  
 使用下列機碼來登錄此資料夾：HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework\v4.0.21006\AssemblyFoldersEx\TreyResearch\\. 為機碼提供此預設值：C:\TreyResearch\Extensions4。  
  
> [!NOTE]
> .NET Framework 版本的組建編號可能不同。  
  
 若要在 64 位元電腦上登錄 32 位元組件，請使用 Wow6432 節點，例如：HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework\v4.0.21006\AssemblyFoldersEx\TreyResearch\\.  
  
## <a name="see-also"></a>另請參閱  
 [Visual Studio 整合](../msbuild/visual-studio-integration-msbuild.md)
