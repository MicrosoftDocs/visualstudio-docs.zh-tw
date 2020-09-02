---
title: 使用 DebuggerTypeProxy 屬性 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- attributes [C#], debugger
- DebuggerTypeProxyAttribute class
- DebuggerTypeProxy attribute
ms.assetid: 943f3bb1-993e-4800-a47e-0af78b063014
caps.latest.revision: 27
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f6e349dd5bea4e0d89c31864960a5438d1e2b13f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "65684078"
---
# <a name="using-debuggertypeproxy-attribute"></a>使用 DebuggerTypeProxy 屬性
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

DebuggerTypeProxyAttribute] (assetId:///T:System.Diagnostics.DebuggerTypeProxyAttribute?qualifyHint=False&autoUpgrade = True) 指定類型的 proxy 或獨立，並變更在偵錯工具視窗中顯示類型的方式。 當您檢視有 Proxy 的變數時，Proxy 會替代 [顯示]**** 中的原始類型。 偵錯工具變數視窗只會顯示 proxy 型別的 Public 成員。 私用成員不會顯示。  
  
 這個屬性可以套用至：  
  
- 結構  
  
- 類別  
  
- 組件  
  
  類型 Proxy 類別必須具有建構函式，才能接受 Proxy 將取代之類型的引數。 每次需要顯示目標類型的變數時，偵錯工具都會建立類型 Proxy 類別的新執行個體。 這種行為可能會影響效能。 因此，除非絕對必要，否則不要在建構函式中再執行任何作業。  
  
  為了將效能的負面影響降到最低，除非使用者在偵錯工具視窗中按一下 + 符號展開類型或使用 <xref:System.Diagnostics.DebuggerBrowsableAttribute>，否則運算式評估工具不會檢查類型顯示 Proxy 的屬性。 因此，您不應該將屬性放在顯示類型本身上， 屬性可以而且應該用於顯示類型的主體中。  
  
  讓類型 Proxy 成為做為屬性目標之類別內的私用巢狀類別，會是較理想的做法。 這樣就可方便它存取內部成員。  
  
  如果在組件層級使用 <xref:System.Diagnostics.DebuggerTypeProxyAttribute>，則 `Target` 參數會指定 Proxy 將要取代的類型。  
  
  如需如何搭配和使用這個屬性的範例 <xref:System.Diagnostics.DebuggerDisplayAttribute> <xref:System.Diagnostics.DebuggerTypeProxyAttribute> ，請參閱[使用 DebuggerDisplay 屬性](../debugger/using-the-debuggerdisplay-attribute.md)。  
  
## <a name="using-generics-with-debuggertypeproxy"></a>使用泛型搭配 DebuggerTypeProxy  
 對泛型僅提供有限的支援。 對 C# 來說，`DebuggerTypeProxy` 只支援開啟類型。 開啟類型也稱為未建構類型，是尚未使用其型別參數的引數具現化的泛型類型。 不支援封閉類型 (也稱為建構類型)。  
  
 開啟類型的語法如下所示：  
  
 `Namespace.TypeName<,>`  
  
 如果您在 `DebuggerTypeProxy` 中使用泛型類型做為目標，就必須使用此語法。 `DebuggerTypeProxy` 機制會自動推斷型別參數。  
  
 如需 c # 中開啟和關閉型別的詳細資訊，請參閱 [c # 語言規格](https://msdn.microsoft.com/library/e5d5a5cc-636b-4bff-b9c8-a8edc6207c22)20.5.2 開啟和關閉類型一節。  
  
 Visual Basic 沒有開放類型語法，因此無法在 Visual Basic 中執行相同的動作。 您必須改用開放類型名稱的字串表示。  
  
 `"Namespace.TypeName'2"`  
  
## <a name="see-also"></a>另請參閱  
 [使用 DebuggerDisplay 屬性](../debugger/using-the-debuggerdisplay-attribute.md)   
  [使用偵錯工具顯示屬性增強偵錯功能](https://msdn.microsoft.com/library/72bb7aa9-459b-42c4-9163-9312fab4c410)
