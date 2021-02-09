---
title: '使用 [編輯後繼續] (c # ) |Microsoft Docs'
description: 在進行偵錯工具時，您可以使用 [編輯後繼續] 來進行程式碼的變更，並將變更套用到中斷模式，而不需在 Visual Studio 中停止再重新開機。
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: ed538c49aeb1257b165d7cfecab0352dd0deb488
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99889170"
---
# <a name="how-to-use-edit-and-continue-c"></a>如何：使用編輯後繼續 (C#)
您可以使用 [編輯後繼續]，在進行偵錯工具時，對程式碼進行變更並套用變更，而不需要停止和重新開機偵錯工具會話。

當您在中斷模式中進行程式碼變更時，c # 的 [編輯後繼續] 會自動發生，然後使用 **continue**、 **Step** 或 **Set Next 語句** 繼續進行偵錯工具，或在偵錯工具視窗中評估函數。

如需詳細資訊，請參閱 [ (Visual c # ) ](../debugger/edit-and-continue-visual-csharp.md)的 [編輯後繼續]。

>[!NOTE]
>優化、混合或 SQL Server common language runtime (CLR) 整合程式碼不支援 [編輯後繼續]。 如需其他不支援案例的詳細資訊，請參閱 [ (c # 和 Visual Basic) 支援的程式碼變更 ](../debugger/supported-code-changes-csharp.md)。 如果您嘗試編輯並繼續進行上述其中一種情況，則會出現訊息方塊，指出不支援 [編輯後繼續]。

**若要啟用或停用 [編輯後繼續]：**

1. 如果您是在調試進程中，請停止調試 (**Debug**  >  **停止調試** 或 **Shift** + **F5**) 。

1. 在 [**工具**  >  **選項**] (或 [**調試**  >  **選項**]) > 的  >  **[一般**] 檢查，請選取或清除 [**啟用編輯後繼續**] 核取方塊。

當您啟動或重新開機調試過程時，此設定就會生效。

**若要使用 [編輯後繼續]：**

1. 在中斷模式中進行偵錯工具時，請變更您的原始程式碼。

1. 在 [ **調試** 程式] 功能表中，按一下 [ **繼續**]、[ **逐步執行** **] 或 [設定下一個語句**]，或在偵錯工具視窗中評估函數。

   偵錯工具會繼續進行新的編譯器代碼。

[編輯後繼續] 不支援某些類型的程式碼變更。 如需詳細資訊，請參閱 [ (c # 和 Visual Basic) 支援的程式碼變更 ](../debugger/supported-code-changes-csharp.md)。
