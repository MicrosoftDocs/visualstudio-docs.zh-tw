---
title: 互通性警告 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.Interoperabilityrules
helpviewer_keywords:
- managed code analysis warnings, interoperability warnings
- interoperability warnings
- warnings, interoperability
ms.assetid: 95de6eb3-40c4-4063-9f59-25cb70e3b2b3
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: fd914a65ff23b05130cb0c36162bb96a3d30aa52
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656495"
---
# <a name="interoperability-warnings"></a>互通性警告
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

互通性警告支援與 COM 用戶端的互動。

## <a name="in-this-section"></a>本章節內容

|規則|描述|
|----------|-----------------|
|[CA1400：P/Invoke 進入點應該存在](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)|公用或受保護的方法是使用 System.Runtime.InteropServices.DllImportAttribute 屬性來標記。 有可能是找不到 Unmanaged 程式庫，或是方法不符合程式庫中的函式。|
|[CA1401：不應顯示 P/Invokes](../code-quality/ca1401-p-invokes-should-not-be-visible.md)|公用類型中的公用或受保護方法具有 System.runtime.interopservices.outattribute. DllImportAttribute 屬性（也會由 Visual Basic 中的 Declare 關鍵字來執行）。 但不得公開 (Expose) 此類方法。|
|[CA1402：避免在 COM 可見介面中多載](../code-quality/ca1402-avoid-overloads-in-com-visible-interfaces.md)|當多載方法會對 COM 用戶端公開 (Expose) 時，只有第一個方法多載會保留它的名稱。 後續的多載則會透過將名稱附加至底線字元 (_) 和對應於多載宣告之順序的整數，重新命名為唯一的名稱。|
|[CA1403：自動配置類型不應該是 COM 可見](../code-quality/ca1403-auto-layout-types-should-not-be-com-visible.md)|COM 可見的實值型別會使用設定為 Layoutkind.sequential 標示的 System.runtime.interopservices.outattribute. StructLayoutAttribute 屬性來標記。這些類型的配置可能會在 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 版本之間變更，而這會中斷需要特定配置的 COM 用戶端。|
|[CA1404：在 P/Invoke 之後立即呼叫 GetLastError](../code-quality/ca1404-call-getlasterror-immediately-after-p-invoke.md)|呼叫 Marshal.getlastwin32error 方法或對等的 [!INCLUDE[TLA2#tla_win32](../includes/tla2sharptla-win32-md.md)] GetLastError 函式，而直接上一個呼叫不是平台叫用方法。|
|[CA1405：COM 可見類型的基底類型應該是 COM 可見](../code-quality/ca1405-com-visible-type-base-types-should-be-com-visible.md)|COM 可見類型會衍生自不是 COM 可見的類型。|
|[CA1406：避免對 Visual Basic 6 用戶端使用 Int64 引數](../code-quality/ca1406-avoid-int64-arguments-for-visual-basic-6-clients.md)|Visual Basic 6 COM 用戶端無法存取64位整數。|
|[CA1407：避免在 COM 可見類型中使用靜態成員](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)|COM 不支援靜態方法。|
|[CA1408：不要使用 AutoDual ClassInterfaceType](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md)|使用雙重介面 (Dual Interface) 的類型可讓用戶端繫結至特定的介面配置。 在未來版本中，若類型或任何基底類型 (Base Type) 的配置有所變更，將會中斷繫結至此介面的 COM 用戶端。 根據預設，如果未指定 ClassInterfaceAttribute 屬性，則會使用分派介面。|
|[CA1409：COM 可見類型應該是可建立的](../code-quality/ca1409-com-visible-types-should-be-creatable.md)|特別標示為 COM 可見的參考類型 (Reference Type) 包含公用參數化建構函式，但不包含公用預設 (無參數) 建構函式。 COM 用戶端無法建立沒有公用預設建構函式的類型。|
|[CA1410：應該和 COM 註冊方法對應](../code-quality/ca1410-com-registration-methods-should-be-matched.md)|類型會宣告使用 <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> 屬性標記的方法，但不會宣告使用 <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName> 屬性標記的方法，反之亦然。|
|[CA1411：COM 註冊方法不應該為可見的](../code-quality/ca1411-com-registration-methods-should-not-be-visible.md)|使用 System.runtime.interopservices.outattribute. System.runtime.interopservices.comregisterfunctionattribute 屬性或 System.runtime.interopservices.outattribute. ComUnregisterFunctionAttribute 屬性所標記的方法，會在外部顯示。|
|[CA1412：ComSource 介面必須標記為 IDispatch](../code-quality/ca1412-mark-comsource-interfaces-as-idispatch.md)|類型是使用 System.Runtime.InteropServices.ComSourceInterfacesAttribute 屬性來標記，而且至少其中一個指定的介面不是使用設為 ComInterfaceType.InterfaceIsIDispatch 的 System.Runtime.InteropServices.InterfaceTypeAttribute 屬性來標記。|
|[CA1413：避免在 COM 可見實值型別中使用非公用欄位](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)|COM 可見實值類型的非公用執行個體欄位對 COM 用戶端而言是可見的。 請檢閱不應該公開之資訊的欄位內容，或是會造成未預期的設計或安全性結果的欄位內容。|
|[CA1414：以 MarshalAs 標記布林值 P/Invoke 引數](../code-quality/ca1414-mark-boolean-p-invoke-arguments-with-marshalas.md)|布林資料類型在 Unmanaged 程式碼中有多種表示。|
|[CA1415：正確宣告 P/Invokes](../code-quality/ca1415-declare-p-invokes-correctly.md)|此規則會尋找以具有重迭結構參數指標之 [!INCLUDE[TLA2#tla_win32](../includes/tla2sharptla-win32-md.md)] 函式為目標的平台叫用方法宣告，而且對應的 managed 參數不是指向 <xref:System.Threading.NativeOverlapped?displayProperty=fullName> 結構的指標。|
