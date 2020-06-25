---
title: '如何-使用編輯後繼續（c #） |Microsoft Docs'
ms.date: 10/04/2018
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Edit and Continue [C#], about Edit and Continue
ms.assetid: 40e136d8-a08c-43bd-b313-fb821c55eb3c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: a88cff54679ac0deae32bfeeff1dd96526f19ea7
ms.sourcegitcommit: c076fe12e459f0dbe2cd508e1294af14cb53119f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2020
ms.locfileid: "85348856"
---
# <a name="how-to-use-edit-and-continue-c"></a>如何：使用編輯後繼續 (C#)
使用 [編輯後繼續] 時，您可以在進行調試時，于中斷模式中對程式碼進行變更並加以套用，而不需要停止並重新啟動偵錯工具。

C # 的 [編輯後繼續] 會在您以中斷模式進行程式碼變更時自動發生，然後使用 [**繼續**]、[**逐步**執行 **] 或 [設定下一個語句**]，或在偵錯工具視窗中評估函式來繼續進行

如需詳細資訊，請參閱[編輯後繼續（Visual c #）](../debugger/edit-and-continue-visual-csharp.md)。

>[!NOTE]
>優化、混合或 SQL Server common language runtime （CLR）整合程式碼不支援 [編輯後繼續]。 如需其他不支援案例的詳細資訊，請參閱支援的程式[代碼變更（c # 和 Visual Basic）](../debugger/supported-code-changes-csharp.md)。 如果您嘗試編輯並繼續進行上述其中一種情況，則會出現訊息方塊，指出不支援 [編輯後繼續]。

**若要啟用或停用 [編輯後繼續]：**

1. 如果您是在調試進程中，請停止調試（[**調試**] [  >  **停止調試**] 或**Shift** + **F5**）。

1. 在 [**工具**  >  **選項**] （或 [**調試**  >  **選項**]）中 > **Debugging**  >  **[一般**]，選取或清除 [**啟用編輯後繼續**] 核取方塊。

當您啟動或重新開機調試過程時，設定就會生效。

**若要使用 [編輯後繼續]：**

1. 在 [中斷模式] 中進行偵錯工具時，對您的原始程式碼進行變更。

1. 從 [**調試**程式] 功能表中，按一下 [**繼續**]、[**逐步執行** **] 或 [設定下一個語句**]，或在偵錯工具視窗中評估函式。

   以新的編譯器代碼繼續進行的偵錯工具。

[編輯後繼續] 不支援某些類型的程式碼變更。 如需詳細資訊，請參閱支援的程式[代碼變更（c # 和 Visual Basic）](../debugger/supported-code-changes-csharp.md)。
