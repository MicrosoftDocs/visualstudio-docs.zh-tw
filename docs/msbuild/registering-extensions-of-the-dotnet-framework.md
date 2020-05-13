---
title: 登錄 .NET Framework 的擴充功能 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Add References dialog box, registering extensions of the .NET Framework
- MSBuild, registering extensions of the .NET Framework
- .NET Framework extensions, registering
ms.assetid: deee6f53-ea87-4b88-a120-bea589822e03
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: e7f79e04cc9afb4238c9f6292a99da684066a7d5
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "77632858"
---
# <a name="register-extensions-of-the-net-framework"></a>登錄 .NET Framework 的擴充功能

您可以開發組件來擴充特定版本的 .NET Framework。 若要讓組件出現在 Visual Studio 的 [加入參考]**** 對話方塊中，您必須將包含該組件的資料夾加入至系統登錄。

 例如，假設 Trey Research 公司所開發的程式庫會擴充 .NET Framework 4，並想讓程式庫組件在專案以 .NET Framework 4 為目標時出現在 [加入參考]**** 對話方塊中。 還假定程式集是在 32 位電腦上運行的 32 位程式集或 64 位電腦上運行的 64 位程式集，並且它們將安裝在*C：_TreyResearch_擴展4\\*資料夾中。

 使用此金鑰註冊此資料夾 **：HKEY_LOCAL_MACHINE_SOFTWARE_Microsoft\\。NETFramework_v4.0.21006_組裝資料夾Ex_TreyResearch\\**。 給鍵這個預設值 **：C：\TreyResearch_擴展4。**

> [!NOTE]
> .NET Framework 版本的組建編號可能不同。

 要在 64 位電腦上註冊 32 位程式集，請使用 Wow6432 節點，例如 **：HKEY_LOCAL_MACHINE_SOFTWARE_Wow6432Node_Microsoft\\。NETFramework_v4.0.21006_組裝資料夾Ex_TreyResearch\\**。

### <a name="see-also"></a>另請參閱

- [視覺化工作室集成](../msbuild/visual-studio-integration-msbuild.md)
