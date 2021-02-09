---
title: 登錄 .NET Framework 的擴充功能 | Microsoft Docs
description: 瞭解如何新增包含元件的資料夾，以將特定版本的 .NET Framework 延伸至系統登錄。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Add References dialog box, registering extensions of the .NET Framework
- MSBuild, registering extensions of the .NET Framework
- .NET Framework extensions, registering
ms.assetid: deee6f53-ea87-4b88-a120-bea589822e03
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 61197fcfe84c96eed2c46b662f93a06386bb9c1e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99931836"
---
# <a name="register-extensions-of-the-net-framework"></a>登錄 .NET Framework 的擴充功能

您可以開發組件來擴充特定版本的 .NET Framework。 若要讓組件出現在 Visual Studio 的 [加入參考] 對話方塊中，您必須將包含該組件的資料夾加入至系統登錄。

 例如，假設 Trey Research 公司所開發的程式庫會擴充 .NET Framework 4，並想讓程式庫組件在專案以 .NET Framework 4 為目標時出現在 [加入參考] 對話方塊中。 也假設元件是在32位電腦上執行的32位元件，或在64位電腦上執行的64位元件，而且這些元件會安裝在 *C:\TreyResearch\Extensions4 \\* 資料夾中。

 使用此機碼註冊此資料夾： **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\ 。NETFramework\v4.0.21006\AssemblyFoldersEx\TreyResearch \\**。 提供此預設值給金鑰： **C:\TreyResearch\Extensions4**。

> [!NOTE]
> .NET Framework 版本的組建編號可能不同。

 若要在64位電腦上註冊32位元件，請使用 Wow6432 節點，例如： **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\ 。NETFramework\v4.0.21006\AssemblyFoldersEx\TreyResearch \\**。

### <a name="see-also"></a>另請參閱

- [Visual Studio 整合](../msbuild/visual-studio-integration-msbuild.md)
