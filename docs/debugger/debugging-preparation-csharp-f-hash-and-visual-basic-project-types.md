---
title: 準備 debug C#、 F#和 VB 專案 |Microsoft Docs
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Basic]
- debug builds, project settings
- Visual C# projects, debugging
- Visual Basic projects, debugging
- debugging [C#]
- debugger, settings by project type
ms.assetid: 7a0535f6-1cd4-4b51-ad34-f4a45b9f1ce3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 90e108ddd64a9b520c8ae1d0c86e416dea64e5be
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738123"
---
# <a name="debugging-preparation-c-f-and-visual-basic-project-types"></a>偵錯準備：C#、F# 和 Visual Basic 專案類型
本章節內的主題說明如何偵錯由 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 專案範本所建立的 C#、F# 和 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 專案類型。

 請注意，建立 Dll 作為其輸出的專案類型，因為它們共用的常見功能而被分組到[偵錯工具 DLL 專案](../debugger/debugging-dll-projects.md)。

## <a name="in-this-section"></a>本章節內容
 [建議的屬性設定](../debugger/managed-debugging-recommended-property-settings.md)本節說明C#、 F#和 Visual Basic 專案的建議與偵錯工具相關的屬性設定。

 [Windows Forms 應用程式](../debugger/debugging-preparation-windows-forms-applications.md)描述 Windows 應用程式專案，並提供偵錯工具、變更預設的 Debug 設定，以及啟動 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 外部的應用程式，並將其附加至其中的指示。

 [主控台專案](../debugger/debugging-preparation-console-projects.md)提供調試C#程式或 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 主控台應用程式的其他考慮。 包括指定命令列引數、從命令提示字元啟動應用程式、寫入至 [輸出] 視窗，和 [主控台] 視窗的疑難排解。

 [Windows 服務](../debugger/debugging-preparation-windows-services.md)描述 Windows 服務，並提供可讓您對 Windows 服務應用程式進行偵錯工具的連結。

## <a name="related-sections"></a>相關章節
 [偵錯工具設定和準備](../debugger/debugger-settings-and-preparation.md)涵蓋設定和準備，讓您必須執行此工作，才能使用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 偵錯工具來進行程式設計。

 對[Managed 程式碼進行調試](../debugger/debugging-managed-code.md)程式涵蓋以 managed 程式碼撰寫之應用程式的常見調試問題和技術。

## <a name="see-also"></a>請參閱
- [偵錯工具安全性](../debugger/debugger-security.md)