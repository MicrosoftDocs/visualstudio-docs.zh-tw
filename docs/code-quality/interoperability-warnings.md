---
title: 互通性警告
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.Interoperabilityrules
helpviewer_keywords:
- managed code analysis warnings, interoperability warnings
- interoperability warnings
- warnings, interoperability
ms.assetid: 95de6eb3-40c4-4063-9f59-25cb70e3b2b3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e18b8ccbdc688586004a363f16360ace1bb488c9
ms.sourcegitcommit: 1efb6b219ade7c35068b79fbdc573a8771ac608d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2020
ms.locfileid: "78167594"
---
# <a name="interoperability-warnings"></a>互通性警告

互通性警告支援與 COM 用戶端的互動。

## <a name="in-this-section"></a>本節內容

| 規則 | 描述 |
| - | - |
| [CA1400：P/Invoke 進入點應該存在](../code-quality/ca1400.md) | 公用或受保護的方法是使用 System.Runtime.InteropServices.DllImportAttribute 屬性來標記。 有可能是找不到 Unmanaged 程式庫，或是方法不符合程式庫中的函式。 |
| [CA1401：不應顯示 P/Invokes](../code-quality/ca1401.md) | 公用類型中的公用或受保護方法具有 System.runtime.interopservices.outattribute. DllImportAttribute 屬性（也會由 Visual Basic 中的 Declare 關鍵字來執行）。 但不得公開 (Expose) 此類方法。 |
| [CA1402：避免在 COM 可見介面中多載](../code-quality/ca1402.md) | 當多載方法會對 COM 用戶端公開 (Expose) 時，只有第一個方法多載會保留它的名稱。 後續的多載則會透過將名稱附加至底線字元 (_) 和對應於多載宣告之順序的整數，重新命名為唯一的名稱。 |
| [CA1403：自動配置類型不應該是 COM 可見](../code-quality/ca1403.md) | COM 可見的實值型別會使用設定為 Layoutkind.sequential 標示的 System.runtime.interopservices.outattribute. StructLayoutAttribute 屬性來標記。這些類型的配置可能會在 .NET 版本之間變更，這會中斷需要特定版面配置的 COM 用戶端。 |
| [CA1404：在 P/Invoke 之後立即呼叫 GetLastError](../code-quality/ca1404.md) | 呼叫 Marshal.getlastwin32error 方法或對等的 [!INCLUDE[TLA2#tla_win32](../code-quality/includes/tla2sharptla_win32_md.md)] GetLastError 函式，而直接上一個呼叫不是平台叫用方法。 |
| [CA1405：COM 可見類型的基底類型應該是 COM 可見](../code-quality/ca1405.md) | COM 可見類型會衍生自不是 COM 可見的類型。 |
| [CA1406：避免對 Visual Basic 6 用戶端使用 Int64 引數](../code-quality/ca1406.md) | Visual Basic 6 COM 用戶端無法存取64位整數。 |
| [CA1407：避免在 COM 可見類型中使用靜態成員](../code-quality/ca1407.md) | COM 不支援靜態方法。 |
| [CA1408：不要使用 AutoDual ClassInterfaceType](../code-quality/ca1408.md) | 使用雙重介面 (Dual Interface) 的類型可讓用戶端繫結至特定的介面配置。 在未來版本中，若類型或任何基底類型 (Base Type) 的配置有所變更，將會中斷繫結至此介面的 COM 用戶端。 根據預設，如果未指定 ClassInterfaceAttribute 屬性，則會使用分派介面。 |
| [CA1409：COM 可見類型應該是可建立的](../code-quality/ca1409.md) | 特別標示為 COM 可見的參考類型 (Reference Type) 包含公用參數化建構函式，但不包含公用預設 (無參數) 建構函式。 COM 用戶端無法建立沒有公用預設建構函式的類型。 |
| [CA1410：應該和 COM 註冊方法對應](../code-quality/ca1410.md) | 類型會宣告使用 <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> 屬性標記的方法，但不會宣告使用 <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName> 屬性標記的方法，反之亦然。 |
| [CA1411：COM 註冊方法不應該為可見的](../code-quality/ca1411.md) | 使用 System.runtime.interopservices.outattribute. System.runtime.interopservices.comregisterfunctionattribute 屬性或 System.runtime.interopservices.outattribute. ComUnregisterFunctionAttribute 屬性所標記的方法，會在外部顯示。 |
| [CA1412：ComSource 介面必須標記為 IDispatch](../code-quality/ca1412.md) | 類型是使用 System.Runtime.InteropServices.ComSourceInterfacesAttribute 屬性來標記，而且至少其中一個指定的介面不是使用設為 ComInterfaceType.InterfaceIsIDispatch 的 System.Runtime.InteropServices.InterfaceTypeAttribute 屬性來標記。 |
| [CA1413：避免在 COM 可見實值型別中使用非公用欄位](../code-quality/ca1413.md) | COM 可見實值類型的非公用執行個體欄位對 COM 用戶端而言是可見的。 請檢閱不應該公開之資訊的欄位內容，或是會造成未預期的設計或安全性結果的欄位內容。 |
| [CA1414：以 MarshalAs 標記布林值 P/Invoke 引數](../code-quality/ca1414.md) | 布林資料類型在 Unmanaged 程式碼中有多種表示。 |
| [CA1415：正確宣告 P/Invokes](../code-quality/ca1415.md) | 此規則會尋找以具有重迭結構參數指標之 [!INCLUDE[TLA2#tla_win32](../code-quality/includes/tla2sharptla_win32_md.md)] 函式為目標的平台叫用方法宣告，而且對應的 managed 參數不是指向 <xref:System.Threading.NativeOverlapped?displayProperty=fullName> 結構的指標。 |
